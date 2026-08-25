# Existing Project Evaluation

Evaluation date: August 25, 2026. This answers the open pre-implementation question: evaluate existing open-source recording projects, then decide whether to adopt, fork, wrap, or build.

## Candidates evaluated

### Craig (CraigChat/craig)

- The established multitrack Discord voice recorder. ISC license, actively maintained (self-host docs updated Dec 2025, new maintainers announced).
- Multitrack per-speaker recording, 6+ hour sessions, `/join` and `/stop` commands — exactly our control flow.
- Self-hosting is heavyweight: Linux-only, PostgreSQL, Redis, ffmpeg plus many codec tools, Node.js/pm2, OAuth client, and a download web app. The install script is invasive (sudo, systemd, visudo entry).
- It is a full production system, not a small embeddable recorder. Self-hosting all of it to get recording on our production server is possible but commits us to operating Craig's whole stack.

### discord-voice-transcript (meanwebuser/discord-voice-transcript)

- MIT license. A wrapper around self-hosted Craig: Docker-first (Craig + PostgreSQL + Redis in compose), adds optional Whisper transcription and privacy controls.
- Its most valuable artifact is research, not code: a June 2026 test matrix showing that Craig's Dysnomia (Eris fork) receive path is currently the only tested working way to receive Discord voice audio:
  - discord.py + discord-ext-voice-recv: partial/corrupted audio under DAVE
  - JDA + libdave: garbage audio
  - DPP: handshake ok, zero audio
  - discord.js + @discordjs/voice + davey: zero audio
  - Craig + Dysnomia: full per-user audio received
- Project maturity is weak: 0 stars, 0 forks, a single squashed "public source snapshot" commit (dates nulled to Jan 1 2000), unproven maintainer. Adopting it as a dependency would mean trusting an unmaintained wrapper.

## Key technical findings

1. DAVE/MLS encryption is now the hard problem in Discord voice receive. Custom audio-receiving bots currently do not work against DAVE-encrypted channels on any mainstream library. This substantially raises the cost of a "build a minimal custom implementation" path.
2. Stage channels do not use DAVE, while regular voice channels may require it. This is directly relevant: our plan to use Stages rather than voice rooms means a custom bot on a Stage may avoid the DAVE problem entirely. This needs a small live test to confirm.
3. Craig itself works and is maintained, but bringing it in means operating its full stack (PostgreSQL, Redis, web download app).

## Decision

Wrap, do not fork or build:

- Use self-hosted Craig (directly, or via the discord-voice-transcript Docker setup) as the recording engine for the proof of concept.
- Our bot remains a thin layer: operator commands, consent/notice practices, and later transcription. It does not implement audio receive itself.
- Keep the custom Stage recording path open only as a fallback experiment: since Stages reportedly skip DAVE, a minimal custom Stage receiver may still be viable if Craig proves too heavy. Test before building.

## Next step

Smallest viable test: run self-hosted Craig in Docker against the Future Herd production server, record a short multi-speaker Stage session, and confirm usable per-speaker tracks. That test settles both whether Craig works for us and, indirectly, how much weight we are carrying.

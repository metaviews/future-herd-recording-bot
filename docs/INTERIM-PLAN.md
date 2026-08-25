# Interim Recording Plan (Craig.chat hosted)

Decision date: August 25, 2026.

## Decision

For the interim, use the hosted public Craig bot (craig.chat) for all recording — both Stage channels and regular voice rooms. Develop and produce real episodes with it.

Long term, replace with our own custom recording bot. The motivation is not privacy but editing sanity: episodes will be edited, assembled, and published on the production server, and a custom bot lets the recorder's output feed directly into that pipeline. Self-hosting Craig (the earlier "wrap" decision in EVALUATION.md) remains the bridge if needed, but is no longer the near-term goal.

## Why this works for us

- Craig supports both Stage channels and regular voice channels.
- Recording happens on Discord's side; we download per-speaker tracks once, on demand. This suits the farm's poor connectivity — no server-side session to sustain, downloads can happen when the connection allows.
- Zero infrastructure on the production server (which is containerized and has had Docker difficulties).

## Constraints to keep in view

- Recorded audio transits Craig's download servers until it expires there. Acceptable for the interim with clear participant disclosure.
- Consent/notice practice is on us, not Craig.

## Test plan (smallest viable test)

1. Invite the public Craig bot to the Future Herd production server (it needs to be able to join voice/Stage channels; a Stage test may require the bot to be moved to speaker).
2. Short test session in a regular voice room: 2+ speakers, a few minutes, one speaker joining/leaving mid-session.
3. Short test session in a Stage channel: same shape, plus a speaker promotion/demotion if convenient.
4. Download the recordings (FLAC and/or OGG per-speaker tracks), move them to the production server, and confirm they open cleanly in the editing toolchain there.
5. Record what worked: command behavior, Stage quirks, download format choice, file sizes and download time over the farm connection.

Outcome: a proven capture→download→production-server path, and a concrete picture of what the future custom bot must reproduce (track format, naming, metadata) to slot into the editing pipeline.

## Production practice to settle during the interim

- Recording notice/consent wording for participants.
- Which download format we standardize on for editing.
- Session naming and where raw tracks live on the production server.
- What the future custom bot's output contract looks like (per-speaker tracks + session metadata), informed by how editing actually consumes the files.

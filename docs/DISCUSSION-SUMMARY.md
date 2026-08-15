# Discussion Summary

## Context

Future Herd has an existing Discord bot for the server. We discussed whether a bot could assist with podcast production by participating in Discord voice channels and recording/transcribing conversations on the production server where the bot is hosted.

## Technical observations

- Discord bot voice recording is possible in principle, and open-source projects already exist.
- Craig is an established open-source multitrack Discord recorder.
- Other projects combine Discord voice recording with Whisper/Faster-Whisper transcription.
- Discord's current voice encryption and DAVE support make current compatibility an important question; older examples should not be assumed to work.
- Stage channels may be a promising first target because Discord documents them as event-oriented channels and identifies them as an exception to the ordinary end-to-end-encrypted audio/video requirement.
- Stage compatibility still needs to be tested. It is not an established project requirement that recording will work.

## Decisions

### Separate project and bot

The recording capability should be developed as a distinct project and Discord bot, not integrated into the existing Future Herd bot initially.

Reasons:

- Development of the two bots should not affect one another.
- Recording has different operational and failure characteristics from community features.
- The first experiment can remain small and disposable.
- The existing bot can continue to focus on the server and community experience.

The two projects may interact in the future, but no integration is required now.

### Narrow initial scope

The first objective is only to establish whether a separate bot can:

1. Join a designated Future Herd Stage.
2. Start recording when explicitly commanded.
3. Stop recording when explicitly commanded.
4. Save a usable recording to disk on the production server.
5. Report basic success or failure.

Transcription is optional and follows recording verification. It is not part of the initial proof of concept.

### Stage-first testing

Stages are the initial recording target rather than ordinary voice rooms. This is a working hypothesis based on their event-oriented design and possible technical advantages, not a guarantee of easier implementation.

## Explicitly rejected as premature scope

The following were discussed as possible future features but are not requirements:

- Automated consent workflows.
- Producer markers.
- Summaries and show notes.
- Chapter detection.
- Publishing integrations.
- Audience management.
- Event scheduling.
- Complex metadata.
- Automatic mixing or mastering.
- Cross-bot APIs.
- Real-time transcription.
- Complex retention systems.
- General podcast-studio automation.

These may be reconsidered only after the basic recording path is demonstrated and actual needs are known.

## Working principle

Do not design around assumed podcast-production needs. First produce a real, playable recording from a real Stage session. Use that result to determine what the project should become.

## Reference projects and documentation

- Craig: https://github.com/CraigChat/craig
- Discord Voice Transcript: https://github.com/meanwebuser/discord-voice-transcript
- Discord DAVE documentation: https://daveprotocol.com/
- Discord Stage Channels FAQ: https://support.discord.com/hc/en-us/articles/1500005513722-Stage-Channels-FAQ
- Discord audio/video encryption documentation: https://support.discord.com/hc/en-us/articles/25968222946071-End-to-End-Encryption-for-Audio-and-Video

These references are research inputs, not commitments to use any particular project or library.

## Current project status

Repository bootstrap only. No implementation exists yet.
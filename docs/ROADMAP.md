# Roadmap

This roadmap is intentionally short. Each step should produce evidence before the next step adds scope.

## Phase 0 — Repository and deployment decisions

- [x] Create a separate repository and project directory.
- [ ] Decide the implementation language and Discord library.
- [ ] Create a separate Discord application/bot account.
- [ ] Decide where the bot will run on the production server.
- [ ] Define the designated test Stage and the minimum bot permissions.
- [ ] Choose a license after the implementation direction is clearer.

## Phase 1 — Stage connectivity

- [ ] Implement a minimal bot process.
- [ ] Add a command to join the designated Stage.
- [ ] Add a command to leave the Stage.
- [ ] Report connection state and errors in a designated text channel.
- [ ] Verify that the bot can join and leave a current Discord Stage session.

## Phase 2 — Recording proof of concept

- [ ] Add an explicit start-recording command.
- [ ] Add an explicit stop-recording command.
- [ ] Record a short real Stage session to local disk.
- [ ] Confirm the output file exists and is playable.
- [ ] Test more than one speaker.
- [ ] Test a speaker joining or leaving during a recording.
- [ ] Test clean stop/finalization.
- [ ] Document any limitations or failures.

The success criterion for this phase is a usable recording produced by an actual Stage session. Until this is demonstrated, transcription and production features remain hypothetical.

## Phase 3 — Basic operational hardening

Only begin this phase if Phase 2 succeeds.

- [ ] Make output paths and filenames predictable.
- [ ] Handle bot restart or disconnect without silently claiming success.
- [ ] Preserve enough logs to diagnose failed recordings.
- [ ] Add basic configuration through environment variables or a local config file.
- [ ] Document deployment and manual operation.

## Phase 4 — Optional transcription experiment

This is optional and should follow recording verification.

- [ ] Select a transcription approach, starting with a local/offline option if practical.
- [ ] Transcribe one completed recording.
- [ ] Compare output quality with the recording.
- [ ] Decide whether transcription belongs in this project or a separate worker.

No further feature roadmap is committed at this stage.

## Explicit non-goals for now

- Complete podcast-production automation.
- Live transcription.
- AI summaries or editorial analysis.
- Publishing workflows.
- General-purpose voice-channel recording.
- Multi-server support.
- A public hosted recording service.

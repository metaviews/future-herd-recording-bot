# Initial Architecture

This document records only the current boundary, not a commitment to a final implementation.

## Components

- Recording bot: a separate Discord application and process for Stage connectivity and explicit recording commands.
- Local output: recording files saved on the production server during the proof of concept.
- Optional later worker: transcription, only after recording is demonstrated.

## Deliberate separation

The existing Future Herd community bot is outside this project. There is no shared code or cross-bot API requirement for the initial version.

## Initial control flow

1. Operator invokes the recording bot's join command.
2. Bot joins the designated Stage.
3. Operator invokes start recording.
4. Bot writes the recording to the configured output directory.
5. Operator invokes stop recording.
6. Bot finalizes the file and reports its path or failure.

The exact command names and implementation language remain undecided.

## Open technical questions

- Which Discord library currently supports the required Stage voice behavior?
- Does the selected library receive usable Stage audio in the current Discord environment?
- Does the bot need special Stage permissions or lifecycle handling?
- What output format is produced reliably?
- Can the bot handle a short session with more than one speaker?
- What happens when a speaker joins, leaves, or is promoted/demoted?

These questions should be answered by a small real test rather than by adding speculative architecture.

## Security and privacy boundary

The bot will not record unless explicitly started. Tokens and credentials must remain in local environment configuration and must never be committed. Recording output should remain outside version control.

The project must still establish an appropriate recording notice and consent practice before use with real participants. This is an operational prerequisite, not an automated feature requirement for the first code milestone.

## Current non-commitments

No decision has been made yet about:

- Python versus TypeScript/Node.js.
- Craig versus a custom implementation.
- Local versus hosted transcription.
- Public versus private recordings.
- Audio format, naming convention, or long-term storage.
- Deployment automation.

Those decisions should follow the Stage recording experiment where possible.

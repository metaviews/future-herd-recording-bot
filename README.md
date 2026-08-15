# Future Herd Recording Bot

A separate, deliberately small Discord bot project for testing and eventually recording Future Herd Stage sessions.

This project is intentionally independent of the existing Future Herd Discord bot. The initial goal is not to build a podcast-production platform. It is to answer one practical question:

> Can an independently deployed bot reliably join a Future Herd Stage and record usable audio to disk on the production server?

## Initial scope

- Separate Discord application, repository, process, and deployment.
- Join a designated Stage channel.
- Start recording only when explicitly commanded.
- Stop recording only when explicitly commanded.
- Save a test recording on the production server.
- Report basic success or failure.
- Consider transcription only after recording has been verified.

## Not currently in scope

- Changes to the existing Future Herd bot.
- Automated consent workflows.
- Producer markers.
- Summaries, show notes, chapters, or publishing integrations.
- Audience management or event scheduling.
- Real-time transcription.
- Automatic mixing or mastering.
- Cross-bot APIs.
- Complex metadata or retention systems.

See `docs/ROADMAP.md` for the narrow verification sequence and `docs/DISCUSSION-SUMMARY.md` for the project context.

## Status

Planning and repository bootstrap. No bot implementation exists yet.

## Principles

- Verify the Discord/Stage recording path before designing features around it.
- Keep this project independent from the community bot.
- Treat assumptions as hypotheses, not requirements.
- Prefer the smallest working test over a broad architecture.
- Do not claim recording works until a real Stage session produces a usable file.

## License

Not yet selected.

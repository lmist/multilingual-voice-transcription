# Multilingual Voice Transcription

An agent skill for transcribing voice messages and recordings that may switch languages. It preserves spoken languages by default, translates on request, and marks uncertain speech without guessing.

Use it for requests such as:

- “Transcribe these voice messages in order.”
- “The speaker switches between English and Arabic; translate the recording into English.”
- “Retry this transcript—the model missed another language.”

The skill works with available transcription tools and providers. An external transcription service may require credentials; keep those in your own environment and never commit them.

## Install

Copy this repository into your agent's user or project skills directory under `multilingual-voice-transcription`, or use a skill installer that accepts a GitHub repository. The entry point is [SKILL.md](SKILL.md).

## Quality

The [evaluation contract](references/eval-contract.md) describes fidelity, language handling, translation, ordering, and uncertainty requirements. The skill's instructions were reviewed by three models; their assessment evaluates the instructions, not guaranteed transcription accuracy.

## License

[MIT](LICENSE).

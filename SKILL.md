---
name: multilingual-voice-transcription
description: Transcribe voice messages or recordings that may switch languages, and translate or organize them as requested. Use for multilingual voice notes, code-switched speech, or retrying a transcript that missed another language.
---

# Multilingual voice transcription

Transcribe the user's recordings in the requested order and output format. The [evaluation contract](references/eval-contract.md) defines the quality bar for evaluating changes to this skill.

1. Identify the requested files and their order. Use filename timestamps when appropriate and say when order is inferred. Check that each requested recording is accessible; report missing files.
2. Choose a speech model capable of the languages and dialects involved. For mixed speech, use multilingual recognition and provide known language, dialect, and subject hints. Do not force one language or treat another language as unintelligible English. Use available tools and honor the user's provider choice. Never expose credentials in logs or outputs.
3. Preserve original languages unless translation is requested, including switches within a sentence. For OpenAI file transcription, check current documentation for model and format support; convert unsupported audio with ffmpeg. Obtain credentials from the environment or existing local configuration without displaying them. If access fails, report it; never invent a transcript.
4. Check output for gaps, suspicious switches, repetition, and technical terms. Reprocess uncertain sections with context or another suitable model when practical. Mark an inaudible span as `[inaudible]`, an unintelligible span as `[unintelligible]`, and an uncertain word as `[word?]`; include timestamps when available and useful. Do not imply that a model transcript was verified by listening if it was not.
5. Label distinguishable speakers consistently when multiple speakers matter. If they cannot be separated reliably, say so rather than inventing identities. Preserve proper names and technical terms where supported; flag uncertain spellings rather than guessing.
6. Translate only when requested. Label the result as a translation, retain meaning and tone, and do not fill gaps by guessing. Preserve a source-language transcript when useful or requested. Keep matching segment boundaries when producing aligned source and translation.
7. Deliver every accessible recording in order, using one file or separate titled files as requested. By default preserve spoken words; light editing means punctuation, capitalization and paragraphing, not paraphrasing. State the editing and translation choices, disclose unresolved uncertainty and missing files, and link output files. Check existing output paths before writing and avoid overwriting unrelated files.

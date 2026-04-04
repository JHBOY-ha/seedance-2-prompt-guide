# Seedance 2.0 Prompt Guide

A skill for crafting high-quality prompts for **Seedance 2.0** (即梦), ByteDance's multimodal AI video generation model.

## Installation

```bash
npx skills add JHBOY-ha/seedance-2-prompt-guide
```

## What it does

When invoked, this skill turns the agent into a Seedance 2.0 prompt engineer. It guides the full prompt creation workflow:

- **Analyzes camera choreography** — before finalizing any prompt, maps out each shot's movement trajectory, subject positions, and timing to catch conflicts early
- **Writes structured prompts** — supports both natural-language 6-step format (simple scenes) and timestamped storyboard format (8s+ or complex scenes)
- **Handles multimodal references** — generates correct `@` syntax for image, video, and audio inputs with explicit role assignments (first frame, character reference, camera reference, etc.)
- **Covers 16 scene types** — characters, product showcases, action sequences, sci-fi effects, music sync edits, dialogue, space exploration, and more
- **Executes via CLI** — when asked to generate, calls the `dreamina` CLI with the correct flags for `image2video` or `multimodal2video`

## When it triggers

- Creating or optimizing Seedance / Jimeng (即梦) video prompts
- Working with ByteDance video model prompts
- Using the `dreamina` CLI for video generation

## Output format

Prompts are output as compact, blank-line-free text ready to paste directly into the Jimeng web interface or pass to the CLI.

## Skill structure

```
seedance-2-prompt-guide/
└── SKILL.md    # Full prompt guide: formulas, camera vocabulary,
                # scene templates, @ reference syntax, CLI usage
```

## Related

- **dreamina** skill — handles Dreamina CLI account setup, credits, and async task management

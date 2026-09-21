# Paper Notes

A portable Markdown collection template and AI skills for organizing scientific literature into clear, evidence-grounded notes. The skills define the workflow and writing conventions; this repository does not include an automation runner.

## Structure

```text
.
|-- SKILL.md                 Main organization and writing rules
|-- skills/                  Read-only auxiliary skills
|-- pending/                 Literature awaiting processing
|-- content/
|   `-- example/
|       |-- assets/          Referenced images and supporting media
|       |-- source/          Original literature files
|       `-- note.md          Note template
`-- index.md                 Global note index
```

## Usage

1. Place original literature files in `pending/`.
2. Ask your AI assistant to read [SKILL.md](SKILL.md) and process the files according to its rules.
3. Review the notes in `content/` and the updated [index](index.md). Processed originals belong in each note's `source/` directory.

Each work uses a separate directory named with lowercase letters, digits, and hyphens. Notes use English headings and the body language requested by the user. The [example note](content/example/note.md) provides a starting template, not a completed literature summary.

## Auxiliary Skills

- [Markdown Usage](skills/markdown-usage/SKILL.md): note structure, formulas, tables, layout, and media.
- [Batch Subagent Workflow](skills/batch-subagent-workflow/SKILL.md): task assignment, review, and integration for large batches, independent of any agent framework.

The directory containing the main `SKILL.md` is the collection root. Relative paths keep the collection portable across platforms. Assistants may read auxiliary skills as needed but must not modify them during note processing.

---
name: paper-notes
description: Recreate the user's paper-note structure and style across platforms, and automate maintenance according to the documented conventions.
---

# Paper Notes

This skill documents the structure and style of the user's paper notes so that both can be reproduced in a new location on any platform. Use these conventions to organize notes and automate their maintenance. Extend this skill incrementally as the user explains their conventions. Do not invent organizational rules for parts the user has not yet described.

## Portability

- This skill is not tied to a fixed workspace, absolute path, operating system, or installation location.
- Treat the directory containing this `SKILL.md` file as the note collection root. Resolve collection paths relative to this directory.
- Document the collection's structure using paths relative to its root so that it can be recreated elsewhere.
- Adapt filesystem paths, shell syntax, and escaping to the platform and tools in use while preserving the documented note structure and style.

## Collection Structure

Keep `pending/`, `content/`, `skills/`, and the global `index.md` directly under the collection root, alongside `SKILL.md`:

```text
<collection-root>/
|-- SKILL.md
|-- skills/
|   |-- <auxiliary-skill-1>/
|   |   `-- SKILL.md
|   `-- <auxiliary-skill-2>/
|       `-- SKILL.md
|-- pending/
|-- content/
|   |-- <descriptive-note-title-1>/
|   |   |-- assets/
|   |   |-- source/
|   |   `-- note.md
|   |-- <descriptive-note-title-2>/
|   |   |-- assets/
|   |   |-- source/
|   |   `-- note.md
|   `-- <descriptive-note-title-3>/
|       |-- assets/
|       |-- source/
|       `-- note.md
`-- index.md
```

- `pending/` holds original literature files awaiting analysis.
- `content/` holds a flat collection of note directories, with no intermediate category directories.
- Name each note directory using lowercase letters, digits, and hyphens. Choose a descriptive title that summarizes the literature and distinguishes it from other entries.
- Each note directory contains `note.md`, `assets/`, and `source/`.
  - `note.md` contains the note itself.
  - `assets/` stores all images and other supporting assets referenced by the note.
  - `source/` stores the original literature files taken from `pending/`.
- The root-level `index.md` is the global index of the notes.

## Auxiliary Skills

The root-level `skills/` directory holds auxiliary skills, each in its own subdirectory with a `SKILL.md` entrypoint and any supporting resources. The skill directories shown above illustrate the structure; they are not required preinstalled skills. Read and use relevant auxiliary skills as needed for the current task.

For Markdown composition, formulas, tables, layout, and media, use [Markdown Usage](skills/markdown-usage/SKILL.md), which provides implementations of this main skill's requirements and renderer-aware syntax guidance.

When processing many pending works in subagent mode, use [Batch Subagent Workflow](skills/batch-subagent-workflow/SKILL.md) for task boundaries, ownership, progress tracking, review, and integration, independently of the specific subagent implementation.

Treat `skills/` and everything inside it as **read-only**. Do not create, edit, overwrite, rename, move, or delete files or directories within it. If an auxiliary skill provides executable helpers, use them only in a way that respects this restriction. Store generated notes, assets, and other outputs outside `skills/`, in the appropriate collection locations.

## Automated Organization

1. Automatically read and analyze the literature files in `pending/`.
2. Create a descriptively named note directory directly under `content/`, following the structure above.
3. Store the analysis in that directory's `note.md`, following the content requirements below, and all referenced images and other supporting assets in its `assets/` directory.
4. Move the processed original literature files from `pending/` into that note directory's `source/` directory.
5. Update the root-level `index.md` to include the corresponding note and link to its `note.md` using a relative path.

## Global Index Format

Keep the root `index.md` a clean index of clickable note links. Include only the index title, category labels or headings, and linked entries; omit explanatory prose, separate summaries, comparison tables, processing status, and maintenance instructions.

Prefer a tree organized as **research field → subcategory → note link**. Subcategories may represent specific method families, literature types (such as surveys or benchmarks), or research tracks. Reuse suitable existing categories and add categories as needed for the actual notes. This hierarchy belongs in the index only; keep note directories flat under `content/`.

Every note entry must contain a working relative Markdown link to its `content/<note-title>/note.md`. Link text may use the literature's title or a concise, faithful summary-style label that distinguishes the work; it need not copy the title verbatim. Keep that summary inside the link text rather than adding an explanation after the link. See [Content and Collection](skills/markdown-usage/references/content-and-collection.md#global-index) for a Markdown example.

## Note Content

Use English for all Markdown headings. Write the body paragraphs in the language requested by the user. If the literature's original title is not in English, retain it in the body and use an English heading.

Every complete `note.md` must contain the following required elements, with conditional sections included when applicable:

- **Title and source context (required):** Include the literature's title and information that explains its provenance, credibility, or significance. Relevant context includes major institutions, authors or other contributors, publication status or venue, and approximate publication date. Use supported facts and distinguish contextual indicators of credibility from evidence for the work's claims.
- **Background and Motivation (required):** Explain the research background, the problem being addressed, and why the work was undertaken.
- **Methods (when applicable):** Explain the approach. Benchmark construction and benchmark structure also belong in this section.
- **Experiments and Conclusions (when applicable):** When the work includes experiments, analyze the experimental setup, experimental resources (including datasets), and results in detail. Draw conclusions from that analysis and distinguish the original work's conclusions from your own interpretation. Include a conclusions section when appropriate to the work.
- **Limitations and Improvements (required):** Discuss the original work's shortcomings and possible improvements. Include independent thinking that goes beyond what the original work states; do not merely repeat its own limitations or future-work discussion. Clearly identify your own critiques and proposals.
- **References (when applicable):** List only related works on which the note strongly depends: works essential to its explanation of a method, evidence, comparison, or analysis. Do not reproduce the original work's bibliography or collect loosely related background citations. Omit this section when no related work meets that criterion. Consult the collection's global `index.md` first; if a referenced work already has a note, preferentially link to that note using a relative path. Otherwise, provide the relevant bibliographic information and an external source link when available.

The English labels above may be used as section headings. Keep required content present even when related topics are grouped or conditional sections are omitted.

## Writing Style

Apply these principles regardless of the language used for the note.

Write from a scientific, rigorous, and objective perspective. Keep claims proportional to the evidence, preserve relevant qualifications, and distinguish reported findings from interpretation. Avoid inappropriate rhetorical devices or embellishment.

Write coherent, direct, readable prose that readers can quickly review and understand. Develop connected paragraphs rather than strings of short, fragmented sentences. Avoid line breaks and structured blocks, such as fenced text or JSON, that interrupt the narrative. Use formatting only when it helps readers grasp the summarized information.

Use examples from the original work, including its appendices, when they help clarify the summarized content. Tables, lists, and indented blocks may also be used to organize information where appropriate. Use these devices in moderation and in accordance with the principles above, preserving continuity in both the narrative and the reader's understanding.

Avoid overusing rhetorical questions, questions immediately answered by the writer, and formulaic contrasts such as "not X, but Y." State the substantive point directly instead of repeatedly relying on these sentence patterns.

Write as a concise synthesis of the literature, not as a lesson or an explanation addressed to the reader. Prioritize the work's substance and the analysis needed to understand it, without conversational guidance or teaching-style scaffolding. Concision must not remove the detailed experimental analysis or other content required above.

## Images and Other Media

Favor a horizontal layout in Markdown notes. When images or other media from the original work are accessible, such as through PDF extraction or screenshots, use them where they improve understanding and help readers quickly locate the corresponding material in the original work. Store referenced media in the note's `assets/` directory and include source locators, such as page numbers or figure identifiers, where available.

Apply the writing-style principles above to media placement as well. Use media in moderation and integrate it with the surrounding discussion without interrupting the narrative or the reader's understanding. Preserve the visual balance of the horizontal layout; do not force a nearly square image into the note when doing so would disrupt that layout merely to include the image.

## Scientific Integrity and Final Review

Ground factual statements and references in accessible evidence. If online sources or referenced literature cannot be accessed, include citation details only when they are explicitly provided in the supplied original files. Do not invent or complete uncertain authors, titles, venues, dates, identifiers, URLs, quotations, or other citation details from guesswork. A reference listed in the supplied work does not establish that its contents have been independently checked; distinguish the supplied work's account of that reference from direct evidence.

Interpret the authors' intent only when the text supports that interpretation. Identify interpretations as such, and avoid unsupported speculation about motives, unstated methods, or missing results. Keep independent critiques and proposed improvements distinct from claims about what the original work actually did.

After completing a note, review it against the available original material to eliminate factual errors caused by hallucination. Resolve unsupported or conflicting statements by correcting them, removing them, or explicitly preserving the uncertainty; do not present unverified details as established facts. Check the following common error points:

- **Identity and publication context:** Verify the title, authors, affiliations, venue, publication status, approximate date, and document version. Do not confuse a preprint with an accepted publication or treat institutional reputation as proof of validity.
- **References and quotations:** Confirm each listed related work is essential to the note's discussion, rather than included merely because the original cites it. Verify citation details and any quoted wording against accessible sources. Do not fabricate missing identifiers or links, or attribute claims to an inaccessible reference based only on its title.
- **Research claims and author intent:** Check that the stated motivation, contributions, and conclusions reflect the source. Separate explicit statements from supported interpretation and from the note's own analysis.
- **Methods and benchmark construction:** Verify procedural details, dataset origins, selection criteria, splits, and evaluation protocols. Do not fill in omitted implementation details with common practice.
- **Experimental settings and resources:** Check model versions, baselines, datasets, sample sizes, hardware, and training or inference settings where reported. Do not substitute assumptions for unreported resources.
- **Numbers and comparisons:** Recheck table and figure values, units, denominators, metric direction, and the distinction between percentages and percentage-point changes. Ensure comparisons refer to compatible settings and that no reported result is assigned to the wrong model or dataset.
- **Strength and scope of conclusions:** Preserve experimental conditions, uncertainty, and limitations. Do not turn correlation into causation, a narrow result into a universal claim, or an observed difference into statistical significance without supporting evidence.
- **Limitations and improvements:** Confirm that criticisms account for relevant material in the main text and appendices. Label proposed improvements as proposals rather than demonstrated outcomes, and do not attribute the note's independent ideas to the authors.
- **Media and source locations:** Check that images, captions, page numbers, and figure or table identifiers correspond to the cited source and version. Ensure crops retain the labels, legends, or qualifications needed to interpret the evidence correctly.
- **Internal references:** Verify that links to existing notes identify the intended work and that relative paths to notes, assets, and original files resolve correctly. Reconcile the global index entry with the completed note, check its research-field/subcategory placement, and remove non-index commentary.

## Interpretation Reminder

English is required for Markdown headings; body text follows the user's requested language, regardless of this skill's language. Coherence means preserving a readable flow, not banning examples, tables, lists, or media: use them selectively when they aid understanding. Write a concise synthesis rather than a tutorial, while retaining required analytical detail. Include conditional sections when applicable, always preserve required content, and never fill gaps in evidence with invented facts.

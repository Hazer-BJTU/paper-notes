# Content and Collection

## Paths and File Roles

Apply the root layout from the main skill. Markdown does not replace the processing workflow: read literature from `pending/`, write the analysis under `content/<note-title>/`, move processed originals into that note's `source/`, and update the root `index.md`.

Use lowercase letters, digits, and hyphens for note directory names. A name should summarize and distinguish the work; an automatically copied full title is not always the clearest choice. Avoid adding category directories beneath `content/`.

Use forward slashes in Markdown link destinations on every platform. Resolve links from the containing Markdown file, not the shell's working directory or the skill directory. Avoid absolute machine paths and `file://` links in the collection.

| Link location | Target | Recommended relative destination |
| --- | --- | --- |
| Root `index.md` | A note | `content/<note-title>/note.md` |
| A note's `note.md` | Its original file | `source/<original-filename>.pdf` |
| A note's `note.md` | Its image | `assets/<figure-filename>.png` |
| A note's `note.md` | A sibling note | `../<related-note-title>/note.md` |
| A note's `note.md` | Global index | `../../index.md` |

Preserve original filenames unless renaming is part of the task. For spaces in a destination, use an angle-bracket destination such as `[Original file](<source/original paper.pdf>)` or percent-encode the space. Encode reserved URL characters when needed, and check the actual target rather than deriving its filename from a display title.

## Required Content and Recommended Forms

| Main-skill requirement | Recommended implementation | Alternative when helpful |
| --- | --- | --- |
| Literature title | One level-one English title | English translation as the heading, original title in body text |
| Provenance, credibility, importance | Opening paragraph with verified contributors, institutions, publication status, and approximate date | A short metadata list followed by a contextual paragraph |
| Background and motivation | `## Background and Motivation` with connected paragraphs | Subheadings only when distinct research questions need separation |
| Methods, if applicable | `## Methods` describing approach and mechanism | `### Benchmark Construction` and `### Benchmark Structure` for benchmark papers |
| Experiments, if present | `## Experiments` with setup, resources, results, and interpretation | Subsections or compact comparison tables for substantial experiments |
| Conclusions, if applicable | `## Conclusions` grounded in the analysis | A clearly identifiable concluding paragraph in `## Experiments and Conclusions` |
| Limitations and independent improvements | `## Limitations and Improvements` connecting each limitation to evidence and a proposal | Separate subsections for substantially different limitations |
| Strongly relied-on related works, if any | `## References` with linked bibliographic entries | Supported footnotes for short asides, with the references still discoverable |
| Original or appendix examples | A short contextualized passage, quotation, or necessary code excerpt | A small table when comparing several genuinely parallel examples |
| Figures and other media | Local asset embed with adjacent source locator and interpretation | Linked full-resolution asset or media file when embedding is unsuitable |
| Global index | Nested research-field → subcategory → linked-note lists | Category headings with linked lists, preserving the same hierarchy |
| Scientific review | Apply the main skill's review before completion | Keep working checklists outside the finished narrative unless requested |

These are choices of form, not permission to omit required content. Do not create empty sections for inapplicable material. Do not invent publication metadata or experiments to fill a template.

## Adaptable Note Outline

The following outline demonstrates placement, not prose style. Replace all bracketed instructions with source-grounded prose in the requested language, and remove inapplicable sections.

```markdown
# [English Literature Title]

[Original title if different. Verified author or institution context,
publication status or venue, approximate date, and significance.]

[Original document](source/paper.pdf)

## Background and Motivation

[Research context, unresolved problem, and motivation.]

## Methods

[Approach, including benchmark construction and structure if applicable.]

## Experiments

### Setup and Resources

[Protocols, baselines, datasets, metrics, and reported resource constraints.]

### Results and Analysis

[Verified results, comparisons, conditions, and interpretation.]

## Conclusions

[Conclusions supported by the analysis and their scope.]

## Limitations and Improvements

[Evidence-grounded critique and clearly identified independent proposals.]

## References

- [Related work essential to this note](../related-note-title/note.md). [Verified citation details.]
```

For a brief work, use fewer subsections and retain the required material in connected paragraphs. For an experiment-heavy paper, organize separate experiments by research question when that makes the setup and corresponding results easier to associate. Do not detach all findings from their conditions into a single undifferentiated results list.

## Source Context and Independent Analysis

Opening context should explain why the source is identifiable and relevant. Keep claims about importance proportional to evidence; a prominent affiliation is context, not a validation badge. Distinguish release dates, revision dates, and publication dates if they differ materially.

Within the limitations section, connect the observed limitation, its consequence, and a proposed improvement. Attribute the authors' own limitations explicitly, then distinguish the note's independent assessment. Do not imply that an untested improvement already works. Avoid visual styles that make speculative statements appear to be established results.

## References and Source Locations

Select references by the note's own dependencies. Include a related work only when the note's explanation, evidence, comparison, or analysis substantially relies on it, such as a foundational method it explains or a baseline it analyzes in depth. A passing mention or inclusion in the original bibliography is insufficient. Do not copy or enumerate the original work's related literature. Omit `## References` when no related work qualifies.

Search the root `index.md` before adding a qualifying reference. Verify that an existing note describes the same work and relevant version, then prefer its relative link. If there is no matching note, include only supported bibliographic information and an available external link. Missing network access does not authorize completing uncertain citation details.

Use source locators near specific claims and figures when useful, for example `Section 3.2`, `Table 2`, or `Appendix B`, localized in body text if appropriate. Distinguish the printed page label from the PDF viewer's page position when they differ. A PDF link such as `source/paper.pdf#page=7` may help in compatible viewers; preserve the page locator in visible text because fragment handling varies.

Heading anchors depend on the renderer. Prefer linking to the related `note.md` itself unless the fragment has been checked. Avoid making access to a reference depend entirely on a footnote extension.

## Global Index

Keep `index.md` limited to its title, category labels or headings, and clickable note links. Prefer nested Markdown lists with research fields as the first level and specific method families, literature types, or research tracks as subcategories. Reuse suitable categories; keep the corresponding `content/` directories flat.

The following is an illustrative structure, not a set of required categories or real notes:

```markdown
# Paper Notes

- Natural Language Processing
  - Retrieval-Augmented Generation
    - [Retrieval-guided evidence selection](content/retrieval-guided-evidence-selection/note.md)
  - Surveys
    - [A Survey of Language Model Evaluation](content/language-model-evaluation-survey/note.md)
- Computer Vision
  - Robustness Benchmarks
    - [Evaluating recognition under distribution shifts](content/recognition-distribution-shifts/note.md)
```

Each note entry must link to an existing `note.md` using its actual root-relative path. Link text may be the literature title or a concise, accurate summary-style label. Do not append summaries, annotations, or explanations outside the link. Exclude comparison tables, introductory prose, processing logs, and maintenance instructions from the index; keep analysis in the notes and operational records elsewhere.

Preserve existing entries when organizing the tree, avoid duplicates, and verify destinations after changing categories or display labels. Markdown headings remain English; list labels follow the requested body language while retaining original titles and technical names when appropriate.

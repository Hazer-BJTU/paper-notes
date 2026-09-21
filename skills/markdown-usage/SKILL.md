---
name: markdown-usage
description: Write and format Markdown paper notes and their global index according to this collection's structure, scientific writing rules, and media conventions. Use when creating, revising, or adapting notes for a Markdown renderer.
---

# Markdown Usage

## Scope and Authority

Read the collection's [main skill](../../SKILL.md) before applying this skill. The main skill defines the required content, scientific standards, language policy, and collection structure; this skill recommends Markdown implementations of those requirements. It does not replace them or introduce a mandatory renderer.

The collection root is the directory containing the **main** `SKILL.md`, two directories above this entrypoint. This auxiliary skill's directory is not the collection root. Treat this directory and its supporting resources as read-only during note work; write notes and media to the collection locations specified by the main skill.

All guidance and syntax examples here are in English. In actual notes, keep Markdown headings in English and write body paragraphs in the user's requested language. Adapt captions, table cells, and list text to that language as well; preserve original titles, quotations, proper names, and technical notation where needed for accuracy. Examples are illustrative, not evidence about any real paper.

## Working Procedure

1. Read the main skill and inspect the target note, global index, available original files, and any established rendering conventions. Determine the requested language and level of detail from the task context.
2. Consult [Content and Collection](references/content-and-collection.md) when creating a note, choosing sections, linking original files or related notes, or updating the index. It maps every structural requirement of the main skill to Markdown options.
3. Consult [Syntax and Mathematics](references/syntax-and-mathematics.md) for paragraphs, headings, links, lists, quotations, tables, formulas, and optional extensions. Use only extensions supported by the target renderer; when unknown, retain a readable CommonMark baseline and disclose necessary dependencies.
4. Consult [Layout and Media](references/layout-and-media.md) when choosing tables versus prose, adapting to rendering width, embedding figures or other media, or preparing portable output.
5. Write a connected scientific synthesis, introducing structured elements with enough context and explaining their implications in adjacent prose. Keep required analysis visible and complete.
6. Perform the main skill's scientific review, then the formatting review below. If a rendering preview is available, inspect it at the intended width and a narrower width. If it is unavailable, report that rendering was not verified rather than claiming visual validation.

## Formatting Review

- Confirm the required title, source context, motivation, and independent limitations analysis are present; include applicable methods, experiments, conclusions, and references.
- Check English headings, requested body language, logical heading levels, paragraph continuity, and moderate use of lists, tables, examples, and media.
- Resolve relative links from the file that contains them, including paths to `assets/`, `source/`, sibling notes, and index entries. Check filename case as well as existence.
- Verify formula delimiters, symbols, units, table alignment, escaped characters, closed fences, and extension support. Preserve meaning when changing notation or layout.
- Check that images remain legible, proportionate, and correctly attributed; captions and crops must retain relevant evidence and qualifications.
- Check for overflow, accidental code indentation, forced line breaks, enormous figures, and long tables that overwhelm the reading flow. Keep essential content out of collapsed blocks.
- Remove instructional placeholders from finished notes. Do not copy illustrative bibliographic details, numerical results, or figure locators as if they were source facts.

## Interpretation

The syntax demonstrations in the reference files teach the AI how to format notes; they are not a model for turning every note into a syntax guide. Prefer connected prose, use structure to aid scanning, and preserve scientific detail. A horizontal layout should make good use of available width without forcing a fixed-width page, distorted media, or uninterrupted lines that overflow.

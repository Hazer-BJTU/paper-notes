# Layout and Media

## Horizontal Layout and Rendering Width

Interpret the main skill's horizontal layout preference as using available reading width effectively while maintaining a continuous document flow. It does not require a landscape page, multiple columns, fixed pixel widths, or horizontally scrolling prose. Markdown source line length does not determine rendered width; the reader's renderer, theme, viewport, and export settings control it.

Use the target preview where available. If the user gives a specific device, renderer, or export width, adapt to it. If unspecified, choose a portable single-column document and avoid brittle sizing. Do not claim a layout has been inspected when only Markdown source was checked.

| Situation | Recommended adjustment |
| --- | --- |
| Wide desktop reading area | Use concise comparison tables and landscape figures when labels remain readable |
| Narrow pane or mobile viewport | Reduce table columns, split comparisons into coherent groups, shorten headers with definitions nearby, and preserve all important values |
| Long equation | Use a meaningful multiline equation or define repeated subexpressions without changing the mathematics |
| Large image with small labels | Show a useful detail with a source locator and link the full-resolution figure |
| Long literal excerpt | Keep only the necessary excerpt and link its full source; do not manually wrap syntax in ways that corrupt it |
| Print or PDF export | Preview the actual export for clipped tables, detached captions, equation overflow, and page-break problems |

Adapt layout before reducing substantive coverage. A narrow screen is not a reason to remove experimental conditions or independent analysis. If the user asks for a shorter note, compress repetition and peripheral detail first, keeping the main skill's required content.

Avoid forced `<br>` breaks in normal paragraphs, repeated separators, empty headings, or space characters used for alignment. Do not force full-width figures merely to fill the page. Do not introduce custom CSS or fixed multi-column layouts unless the user's output requirements call for them and the renderer supports them.

## Choosing Prose, Tables, and Lists

Use prose when the relationship among claims matters: motivation, cause, caveat, interpretation, and limitations generally need sentences. Use a table when the reader should compare repeated fields across methods or resources. Use a list for independent parallel facts or a genuine sequence. A requested format can change the presentation without weakening scientific qualifications.

When a table becomes too wide, first remove redundant columns, move shared setup into adjacent prose, and shorten headers without losing units or metric direction. Then split by a meaningful dimension, repeating the identifying column so readers can associate rows. Do not split in a way that hides which settings produced which results. Avoid moving all caveats into distant footnotes.

When a list becomes a sequence of dense mini-essays, promote meaningful topics to subsections or combine them into connected paragraphs. When converting prose to a table at the user's request, preserve uncertainty and exceptions in cells or nearby text. Do not fabricate values to make rows uniform. If the renderer does not support tables, use short labeled entries rather than monospaced ASCII tables that will overflow on narrow screens.

## Selecting and Acquiring Media

Use accessible original figures, tables, examples, and appendix material when they clarify the analysis or help locate evidence. Extract from the original file or capture a faithful screenshot where the available tools permit. Choose individual relevant figures or panels instead of inserting entire pages by default.

Store referenced media under the note's `assets/`. Use descriptive filenames such as `figure-3-evaluation-overview.png` when the figure number is verified. Keep original literature under `source/`. Prefer local assets over fragile remote image embeds; an external source link can accompany a locally stored asset. If the material cannot be accessed, do not invent a figure, caption, or locator.

Preserve aspect ratio, legends, axes, units, panel identifiers, and qualifications needed to interpret the evidence. Cropping whitespace can improve use of width; removing unfavorable data or essential caveats changes the evidence and is unacceptable. Label crops and adaptations, and keep the complete source reachable. A chart reconstructed from data needs verified values and an explicit reconstruction label, not the appearance of an original figure.

PNG is often suitable for text-heavy screenshots and diagrams; JPEG can suit photographic material. Use SVG when the renderer supports it and it preserves the intended figure correctly. These are practical options, not mandatory conversions. Check the displayed result rather than assuming that a file extension ensures legibility.

## Standard Image Placement

Place the image near the paragraph that motivates it, followed by a brief caption and interpretation as needed:

```markdown
[Paragraph explaining the comparison supported by this figure.]

![Concise description of the evidence shown](assets/figure-3.png)

Figure 3 from the original work, Section 4, PDF page 7.
[Original document](source/paper.pdf#page=7).

[Paragraph interpreting the relevant result and its limits.]
```

The figure number, section, and page above are illustrative and must be replaced with verified locators. Captions and alternative text should follow the requested body language. Alternative text should convey the image's purpose or information, not just repeat its filename. A caption is an ordinary adjacent paragraph in portable Markdown; native figure numbering is not guaranteed.

Link a preview to its larger original when useful:

```markdown
[![Evaluation overview](assets/evaluation-preview.png)](assets/evaluation-full.png)
```

Do not duplicate the same graphic at several scales unless the additional view contributes distinct information. Keep conclusions in readable text even when a chart supplies the evidence.

## Size, Proportion, and Square Images

Standard Markdown image syntax has no portable size controls. Prefer assets that remain useful under the renderer's normal image behavior. A naturally wide figure often fits the intended layout well; a nearly square figure may be shown smaller, linked separately, or omitted when it adds little.

Do not stretch a square image into a landscape shape or crop meaningful content merely to obtain a preferred ratio. Side-by-side panels are appropriate only when they form a real comparison, the renderer supports the arrangement, and labels remain legible at the target width. Avoid using Markdown tables solely as an image positioning grid.

If HTML is supported, an image width can be specified, but verify the result and narrow-width behavior:

```html
<img src="assets/figure-3.png" alt="Description of the evidence" width="560">
```

This example is conditional, not the default: HTML attributes or styles may be stripped, and the width may overflow without responsive styling. Preserve the aspect ratio by not forcing an incompatible height. Use a standard Markdown image or a descriptive link when the rendering environment is unknown. Do not assume HTML `<figure>`, `<figcaption>`, inline CSS, or flexbox work in every Markdown viewer.

## Other Media and Attachments

Audio, video, interactive figures, and embedded PDFs have no universal Markdown playback syntax. The portable baseline is a descriptive link to a local resource, optionally accompanied by a poster image:

```markdown
[![Demonstration preview](assets/demo-preview.png)](assets/demo.mp4)

[Open the demonstration video](assets/demo.mp4).
[Brief description of the relevant observation and verified timestamp.]
```

Use HTML players or platform embeds only after checking support, and retain a direct link and textual description. Do not autoplay media. For a relevant audio or video excerpt, identify the time span when verified and summarize its evidentiary role; a transcript can help when it is available and accurate.

Link large datasets or supplementary files descriptively rather than pretending that their contents are visible in the Markdown note. Keep any locally stored supporting material in `assets/`, and the supplied original literature files in `source/`, following the main skill's distinctions.

## Final Visual Review

Inspect the intended rendering width and a narrower view when preview tools are available. Check paragraph flow, table headers and wrapping, equations, figure text, captions, link destinations, and whether optional extensions silently degrade to raw syntax. Confirm that essential results remain visible and understandable without opening a collapsed section or playing media.

Visual polish must not change the evidence. Recheck numerical values after transcribing a table, notation after reflowing a formula, and source context after cropping a figure. When preview is unavailable, perform source and link checks and state the unverified rendering limitation.

# Slide Blueprint and Visual Storyboard

Use this reference when designing a new deck or substantially redesigning one. A blueprint should make each page executable without guessing its content or reading path. Deliver the organized blueprint as a companion architecture Markdown file with the finished deck unless the user explicitly excludes it. Raw research logs stay internal. Show a separate storyboard when requested or for a planning-only task; it is not a mandatory approval step.

## Companion architecture Markdown

Save UTF-8 Markdown next to the deck, with a shared filename stem, for example `Topic.pptx` and `Topic_outline.md`. Return both actual files. Draft this document during planning, then update it to describe what was finally produced, not an abandoned outline. Use the requested content language. Do not require the user to supply or approve this document before continuing.

Include:

1. **Brief:** topic, audience, purpose, scope, language, time/slide count, template, and relevant assumptions.
2. **Chapter overview:** chapter, purpose, slide range, and number of slides. Reserve and count a standalone final「謝謝聆聽」slide within the total, even for a short deck, alongside any cover, contents, and chapter dividers. Use this exact closing wording unless the user explicitly overrides the closing wording or language. Markdown headings and production notes are not additional slides.
3. **One entry per slide:** actual position `P01`, `P02`, etc.; slide type; chapter; final title; purpose/prerequisite; exact visible text, table values or equations; selected figure and its page/panel; composition and annotations; speaker notes; and provenance/conditions. Label the on-slide content separately from production directions and notes. Structural pages can have concise entries but must not be omitted. The last slide entry must describe the standalone final「謝謝聆聽」page (or an explicit user wording/language override). Put conclusions, Q&A, sources, credits pages, and appendix/backup entries before it; required template credit may be unobtrusive on the closing.
4. **Sources and assets:** bibliographic references and usable figure/asset links where available. Bundle referenced local assets beside the MD with relative paths when needed for reuse; otherwise provide the source file/page/panel and intended crop. Never link to transient scratch paths or claim an unproduced image exists.

Suggested per-slide shape (adapt labels to the content language):

```markdown
### P01｜封面｜簡報標題

**頁型／章節：** 封面／前置頁
**目的與承接：** ...

**畫面文字**
（填入最終投影片實際文字，不只描述要寫什麼）

**配圖、版面與標記**
（來源頁碼／圖號、裁切範圍、位置、比例與重點標記）

<details>
<summary>講者備註與來源</summary>

講稿：...

來源與必要條件：...

</details>
```

Before delivery, compare the Markdown with the final deck: same total and sequence, one entry per slide, matching titles/numbers, consistent figures, and matching speaker notes. Verify that the final rendered slide and the last slide entry are the same standalone thank-you page, with no later slides, including hidden or backup slides. Keep it clean in the existing template without forcing a decorative visual. Update navigation and chapter counts after any slide insertion/deletion/reorder. When editing an existing deck, synchronize its companion MD or create one from the final deck if none exists, unless the user excludes it. A planning-only document should say it is a plan; a final-deck companion should identify the delivered filename and final slide count.

## Per-slide record

Keep the record compact, but include these decisions for **each** slide:

| Decision | What to specify |
| --- | --- |
| Purpose and takeaway | The question answered and the exact claim or topic title the audience will see |
| Learning dependency | What the audience must already know, where it was explained, and why this slide belongs here |
| Mechanism or comparison | Method: problem, input, operation, output and condition. Result: dataset, metric/direction, baseline, data amount and justified readout |
| Content | Final wording when known; otherwise a clearly labeled placeholder with the required evidence or asset |
| Composition | Each element's role, approximate position and proportion, alignment, and relationship to other elements; identify title, evidence, explanation, source, and any callout without drawing a box around each one |
| Visual treatment | Slide archetype, hierarchy, type scale, colors with semantic meaning, image treatment or chart encoding, and intentional whitespace |
| Image provenance | The source page or file and intended crop for reused evidence; for a generated conceptual visual, its explanatory purpose, composition, and visible illustration label where authenticity could be mistaken |
| Reading path | Where the eye enters, how the evidence is read, and what the viewer should retain |
| Source and notes | Evidence provenance, assumptions, speaker details, and accessibility needs that should not crowd the canvas |

Use proportions or a simple grid to communicate geometry. Pixel coordinates are useful only when a fixed output size or template requires them. Reuse a small set of archetypes, but adapt the composition when the evidence requires it. Do not force every slide into the same arrangement. Plan open space as an intentional part of the layout. Vary rhythm through scale, crop, alignment, and visual weight rather than alternating generic card grids.

## Visual preview

- Render **one frame per slide** at the intended aspect ratio. Show the actual layout, representative type, palette, chart or image areas, and approximate content density. The preview should convey the intended visual character, not merely boxes with labels or a grid of rounded cards.
- Use actual source figures, exact diagrams, or native tables/charts where they best explain the page. Generate an illustration only when it adds comprehension unavailable from the evidence or precise diagram. Keep illustration distinguishable from reported evidence. Text-only structural pages need no decorative visual. Do not leave an asset placeholder when that asset is essential to evaluating the finished composition.
- Use the deck's production route when practical. A draft slide render, PDF page, or image frame is suitable. An HTML or SVG storyboard is also suitable for a planning-only deliverable if it renders reliably. Use supplied brand assets as supplied; do not synthesize a logo or factual image.
- Show frames together as a contact sheet for pacing and consistency, and make individual frames available at a size where text and alignment can be reviewed. When the final deck itself is rendered and inspected, those renders satisfy this preview requirement.
- Put `PLACEHOLDER`, `ILLUSTRATIVE`, or equivalent directly on any unsourced mock content. Keep it visible in both the blueprint and frame. Do not imply that decorative sample data supports a conclusion.
- Compare the frames with the blueprint: each planned element appears, evidence is legible, title and hierarchy match the message, and adjacent slides have a coherent rhythm. Check whether any border, fill, or container earns its place by clarifying structure; remove decorative boxes. Also check for oversized empty areas around small diagrams and repeated networks of equal rounded boxes. Fix crowded or visually thin frames before handing off the design.

The storyboard supports review without requiring a pause in authorized production. It does not replace checking editability, notes, links, accessibility, and export behavior. Final-deck renders satisfy the visual-preview requirement; do not create redundant artifacts.

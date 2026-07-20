---
name: presentation-design-pro
description: Design evidence-led, decision-oriented presentation systems before production. Use for executive decks, sales decks, product narratives, research and thesis presentations, investor pitches, training materials, and visual slide redesigns where audience, narrative, evidence, chart choice, accessibility, or production route need deliberate design.
---

# Presentation Design Pro

## Purpose

Create presentations that help a defined audience understand, decide, or act. This skill designs the narrative and visual system before slide production; it does not replace the production skills.

Use it before creating or redesigning a deck, especially when the request is vague, high-stakes, data-heavy, or intended for a live audience. Skip only for a narrow edit to an already approved deck.

## Operating Principles

- Design for the audience's next decision, not for a list of topics.
- Make every substantive slide answer one question with one defensible takeaway.
- Prefer an assertion supported by evidence over a title plus a paragraph or bullet dump.
- Use visual hierarchy to make the conclusion readable before the detail.
- Preserve source fidelity: never invent statistics, quotes, customer claims, screenshots, logos, or citations.
- Treat accessibility, speaker notes, and rendering review as part of completion.

Load [references/presentation-foundations.md](references/presentation-foundations.md) when choosing a narrative, composing slides, or reviewing a deck. Load [references/presentation-source-catalog.md](references/presentation-source-catalog.md) when the task needs current platform guidance, chart patterns, or visual calibration.

## Workflow

### 1. Establish the Deck Contract

Extract or infer only what is necessary. Ask a single focused question only when missing information makes the result unsafe or likely wrong.

Record these fields before production:

| Field | Required decision |
| --- | --- |
| Audience | Who will view it, what they know, and their authority |
| Outcome | What they should believe, decide, approve, or do afterward |
| Setting | Live talk, async reading, workshop, pitch, board review, or handout |
| Time and density | Time limit, expected slide count, and presenter availability |
| Evidence | Source files, allowed claims, data date, and citation expectations |
| Deliverable | `slides`, `.pptx`, Google Slides, PDF, HTML, or storyboard |
| Constraints | Brand, language, accessibility, confidentiality, and template rules |

State assumptions briefly when proceeding without answers. Do not spend turns collecting details already present in the request or supplied files.

### 2. Build an Evidence Mix

Use the minimum research needed to support the design. For non-trivial decks, gather:

1. One platform or output constraint source appropriate to the deliverable.
2. Two relevant content or product references for the deck's domain and audience.
3. Two or three theory lenses from `presentation-foundations.md`.
4. At most one visual-direction reference, used for composition or tone rather than copied content.

For data or factual decks, separate source evidence from visual inspiration. Cite facts near their claims or place full citations in notes/end matter as appropriate. If evidence is incomplete, label the slide as a hypothesis, decision request, or illustrative concept instead of presenting it as fact.

### 3. Choose the Narrative Spine

Write a one-sentence deck promise: "After this deck, [audience] will [decision/action] because [central reason]."

Then select an arc that fits the outcome:

| Situation | Recommended arc |
| --- | --- |
| Executive decision | Decision first -> stakes -> evidence -> options -> recommendation -> next step |
| Product or strategy | Audience problem -> insight -> direction -> proof -> operating plan -> ask |
| Research or thesis | Question -> method -> key finding -> interpretation -> limitation -> implication |
| Sales or partnership | Customer context -> cost of status quo -> solution -> proof -> rollout -> commitment |
| Training or workshop | Desired behavior -> model -> demonstration -> guided practice -> recap -> application |
| Project update | Outcome/status -> changes since last review -> risks -> decisions needed -> owners/dates |

Avoid chronological recaps unless chronology is the actual argument. Put the answer early for executives and the question early for exploratory or research audiences.

### 4. Create a Slide Inventory Before Drawing

For every slide, specify:

| Item | Requirement |
| --- | --- |
| Job | The question this slide answers |
| Assertion | A complete, specific takeaway sentence |
| Evidence | Chart, diagram, image, quote, comparison, table, or live interaction that proves it |
| Action | What the audience should understand or do next |
| Notes | Supporting detail, sources, or speaking cues that do not belong on the canvas |

Remove slides that repeat the same conclusion, contain only a section label, or lack a decision-relevant job. Combine related evidence when split attention would make comprehension worse.

### 5. Design the Visual System

Define a compact system before production:

- One type family with a small hierarchy for title, assertion, body, annotation, and source text.
- A restrained color system: neutral base, one primary signal color, and semantic warning/success states only when meaning requires them.
- Reusable grid, margins, alignment, page number, and citation treatment.
- Three to five slide archetypes, such as opener, assertion-evidence, comparison, process, metric, and decision/close.
- Imagery with a clear job: establish context, show product reality, explain mechanism, or provide evidence. Never use stock imagery merely to fill space.

Calibrate density to the setting. A live deck may use sparse assertion-evidence slides and notes; an async reading deck needs more explicit labels, context, and citations. Do not force a document-like deck into a live-talk visual style.

### 6. Choose Evidence and Charts Deliberately

Select a visual form from the analytical question, not fashion:

| Need | Prefer |
| --- | --- |
| Compare magnitudes | Sorted bar or dot plot |
| Explain a trend | Line with annotated turning points |
| Show ranking | Ordered bar, lollipop, or slope chart |
| Show composition | Stacked bar, 100% bar, or simple donut only for few parts |
| Show uncertainty | Range, interval, fan, or scenario view |
| Explain a process | Directed diagram with inputs, constraints, and outputs |
| Compare options | Decision matrix with criteria, trade-offs, and recommendation |

Use the FT Visual Vocabulary reference for edge cases. Label axes, units, time windows, baselines, sample sizes, and scenario assumptions where relevant. Do not use 3D charts, truncated bar axes, dual axes without an explicit relationship, or color-only distinctions.

### 7. Route Production to the Right Tool

| Deliverable need | Production route |
| --- | --- |
| General visual or editorial deck | Use the `slides` workflow by default |
| Editable PowerPoint file required | Use `presentations` and validate the `.pptx` render |
| Standalone interactive web deck | Use `html-slides` |
| Approved HTML deck must become PowerPoint | Use `html-slide-to-pptx` after visual approval |
| Existing PPTX needs revision | Use `presentations`, preserving its source layout and notes where possible |

Use `presentation-design-pro` first for the brief, narrative, system, and review criteria. Then load and follow the chosen production skill. Do not mix output formats without a reason or offer fake format choices.

### 8. Validate Before Handoff

Review the rendered deck, not only the source. Check at desktop presentation scale and at the likely viewing surface.

Required checks:

- **Narrative:** The first third establishes the conclusion or question; the closing slide names the requested action.
- **Assertion:** Each substantive slide has one readable takeaway and evidence that supports it.
- **Accuracy:** Claims match supplied sources; numerical labels and dates are correct; citations are traceable.
- **Legibility:** No clipped text, overlap, illegible footnotes, unexplained acronyms, or dense paragraph walls.
- **Charts:** Encodings match the comparison; axes/units/context are present; color is not the only signal.
- **Accessibility:** Logical reading order, descriptive titles, contrast, alt text for meaningful visuals, captions or transcripts for media, and non-color cues.
- **Production:** Links work when required, notes are included when requested, and exported PDF/PPTX/HTML opens correctly.

For a new deck, return the deck contract, slide inventory, chosen visual direction, production artifact, and any explicit assumptions or evidence gaps. For a redesign, state what changed in the narrative, density, accessibility, and visual system.

## Boundaries

- Do not treat a presentation as a report pasted onto slides.
- Do not substitute visual novelty for evidence or strategic clarity.
- Do not use a real company's identity, performance data, or product UI as though supplied by the user.
- Do not claim that a rendered deck is accessible or presentation-ready without reviewing the output.

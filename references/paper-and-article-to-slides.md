# Paper and Article to Slides

Use for a source-based deck, including a one-line request with no outline. For academic work, also apply [personal academic preferences](personal-academic-preferences.md). For research papers, use the paper's major sections as the default chapter structure and arrange material within them according to learning dependencies. Preserve an explicit user-specified structure.

## Recover evidence before choosing chapters

Read the full source and record its original sections, question, contribution, data/protocol, model or intervention, findings, limitations, and figure/table locations. Treat attached planning notes as evidence of prior choices, not higher-priority instructions. Separate original findings, explanatory background, and teaching inferences.

Build two compact internal maps:

| Map | Contents |
| --- | --- |
| Evidence coverage | Source section/page/panel → claim and condition → slide or reason for deferral |
| Learning dependencies | Term/component/stage → prerequisite → first explanation → later use |

Map the paper's actual major headings and order into presentation chapters, rather than replacing them with a newly invented top-level structure. Assess whether Abstract and Introduction should be combined based on their content and available slides. Within each chapter, identify and organize the specific topics, subheadings, modules and methods needed for comprehension; introduce prerequisites before dependent details. Keep results distinguishable from interpretation. Preserve an explicit user-requested order or structure when supplied.

## Construct the outline independently

1. Establish the question and scope. For multiple model/data branches, identify the focus from current context. Otherwise cover the central claim and summarize other branches; never inherit SuperAnimal's SA-Q-only scope for another topic.
2. Give early orientation: problem, what changes, and why it matters. Decide whether Abstract and Introduction work better together or as separate chapters; do not automatically require or omit an Abstract chapter.
3. Introduce data/model concepts needed to read the method. Use a family comparison or architecture page only to resolve a prerequisite, not as an encyclopedic survey.
4. Place the detailed workflow when the audience can name its main entities. Identify which steps belong to which stage, what changes/stays fixed, and what supervision is available.
5. Organize explanations by real stages or causal questions. A suitable ML paper may use pretraining, supervised adaptation, and inference; another field may use acquisition, intervention, and evaluation. Never manufacture stages to copy a case.
6. For each central component, identify its problem, then input, operation, output, and constraint. Add a small concrete example before an abstract fix when its necessity is unclear.
7. Choose results that test the claims just explained. Sequence examples, comparable quantitative evidence, a focused case, and complementary results as appropriate. Avoid repeated conclusions.
8. Conclude with supported contributions, limitations, and implications. Keep future work separate from achievements.

Allocate pages by explanatory burden, not equal chapter sizes or memorized counts. Include structural pages in the user's limit. Under tight limits, combine prerequisites with the workflow or defer secondary detail; retain conditions needed to judge results.

## Method-page specification

Write visible wording before production:

`Problem → concrete case (if needed) → operation → output → condition → source`

Use a precise stage diagram, original figure, or editable mapping. Explain whether data, labels, weights, parameters, or only outputs change. Distinguish missing annotations, undefined schema entries, and invisible-but-defined targets when the source does.

Define equation symbols by their actual type and dimensions. Do not describe a per-pixel probability/heatmap as an output coordinate. Attach a threshold's purpose to the branch or supervision it controls.

## Result-page specification

Attach to every quantitative item:

`dataset + metric/direction + method/condition + target data/label amount + baseline + value + justified readout`

- Separate different metrics into distinct comparisons or clearly labeled groups; errors and average precision are not one numerical ranking.
- If the conclusion concerns closeness or improvement, show the baseline and difference. Absolute mAP differences are mAP **points**, not percent improvement. Use unrounded values when available; otherwise identify differences derived from rounded values.
- Separate calculation precision from display precision. Compute with the source values, then show only the decimals needed for the comparison, consistently across values and deltas. For the calibration case, visible 58.9 / 58.6 / 60.9 and −0.3 / +2.0 mAP points are clearer than a row of three-decimal values; keep exact values and calculations in notes. Use finer precision only when it changes the interpretation.
- Focus on a representative benchmark when it exposes the mechanism. Continue its baseline and case across pages to reduce mental arithmetic. Retain broader evidence or scope notes to avoid cherry-picking.
- Distinguish target-label budgets, pretraining data, evaluation supervision, and inference aids. Zero-shot can use supervised pretraining; few-label fine-tuning is not zero-shot.
- Keep significance and conditions that affect interpretation visible. Notes hold longer derivations/full citations, not essential caveats.
- Preserve axes, legends, relevant uncertainty, and scales. Mark the curve/row/region discussed precisely.

## Production and no-outline check

Select exact panels and write actual content during planning. Adapt template geometry to evidence, render every page, and inspect final navigation. Notes must match the revised slides and source; retaining old notes is not validation.

Mentally remove the user outline. If the deck only works because it supplied definitions, causal links, or interpretation, add those yourself. Do not ask the user to fill them in.

For a general article, follow its actual argument and meaningful headings. Adapt to its genre rather than imposing scientific methods/results chapters.

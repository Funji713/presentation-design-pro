# Personal Academic Presentation Preferences

Learned from `SuperAnimal_old.pptx` (33 slides) and the user's preferred `SuperAnimal_new.pptx` (35 slides), compared with the supplied outline and paper on 2026-10-30. Apply the transferable decisions from planning through production. Do not copy this paper's facts, people, date, language, or slide count into another deck.

The reference user retained most typography, palette, source assets, and template chrome. These are historical observations about the finished example, not a default template supplied to other users. Use an accessible template the current user has supplied, selected, or explicitly configured locally; ask for one only if none is available; do not automatically clone the example's masters, colors, or fonts. The transferable learning is how to teach the material and help the audience read its evidence. A cosmetic restyle alone does not apply that learning.

## Evidence and reusable decisions

| Observed change | Transferable decision | Scope / caution |
| --- | --- | --- |
| old 17–18 (model families, HRNet) moved to new 12–13 before detailed workflow new 14 | Define model/entities before the workflow relies on them | Not every paper needs a backbone survey; early lightweight orientation remains useful |
| old 13 Panoptic divider became new 15 Pretrained Stage; new 19 adds Fine-tuning Stage | Divide dense methods into the stages the speaker explains | Use actual stages; distinguish inference-only search from weight-updating adaptation even if adjacent |
| new 21 adds Nose / Left eye / Tail base mapping and explains why an unsupervised output can still change | Put a concrete missing-information/failure example before the algorithm that addresses it | Preserve causality, not these exact keypoints or unsupported mechanisms |
| old 20 → new 22 emphasizes ground truth, threshold, pseudo-label cell, and replay takeaway | Highlight the exact rule or condition needed to understand the method | Sparse semantic emphasis, not all text red |
| old 22 → new 24 removes a temporal-model comparison, enlarges the source figure, stacks four operations with attached conditions | Give one page one explanatory job; place constraints beside the operation | Remove tangents only when unnecessary to the claim |
| old 26 → new 28 removes mixed-metric Horse-10 row, groups mAP benchmarks, adds differences, outlines iRodent | Make quantities comparable and calculate the readout for the audience | Do not conceal adverse results; retain elsewhere if material |
| old 27 → new 29 focuses on iRodent with baseline/zero-shot/few-label values and label budgets | Continue one case across pages; combine plot, values, and baseline differences | A teaching choice, not a rule to show only the strongest benchmark |
| new 27, 30, 31 enlarge evidence and simplify nearby content | Allocate area to evidence and precise annotations | Preserve legends, metrics, caveats, and traceability |
| Notes change on 14 corresponding pages; new 20 explains per-image then cross-image matching, new 22 explains three supervision cases, new 28–29 explicitly continue the iRodent comparison | Write notes with the slide: resolve likely questions, explain cases, and bridge to the next page | Other 19 corresponding notes were retained; do not claim all narration was rewritten |
| Plain dividers and lavender/cyan/yellow styling remain | Preserve familiar academic rhythm; text-only dividers are acceptable | Retained features show compatibility, not newly proven preference |

## Writing and teaching defaults

- Use topic/method titles, exact terms, and grammatical short clauses. Avoid forced slogans and outcome claims on setup pages.
- Explain the reason for a method on the canvas. A causal sentence is more useful than fragments constrained to a fixed character count.
- Keep model/data/setup distinctions visible. Explain outputs and stage changes before presenting performance.
- Show the evidence and indicate where to look with a row, outline, key term, or curve annotation. Do not depend on unstated presenter narration.
- Let results answer: compared with what, with how much data, and by how much? A dataset/metric/condition can be the clearest title.
- Calculate with source precision but display readable precision. The revised iRodent page uses one decimal for mAP and simple point differences; exact multi-decimal calculations belong in notes unless they affect the conclusion.
- Notes hold fuller explanation, sources, and nuance; essential comparisons and causal links remain visible.
- For live academic talks, write natural speaking notes that connect the prior question, direct attention, explain what changes and why, and lead to the next page. Preserve a separate source block. Avoid fabricated personal experiences and copied presenter identity.

## Visual calibration

These screenshots are design calibration references, not content sources or blank templates for future topics. Inspect the relevant pair when calibrating a method/result page:

- [new 21: causal example](../assets/calibration/new-21.png)
- [old 22](../assets/calibration/old-22.png) → [new 24: focused process](../assets/calibration/new-24.png)
- [old 26](../assets/calibration/old-26.png) → [new 28: comparable evidence](../assets/calibration/new-28.png)
- [old 27](../assets/calibration/old-27.png) → [new 29: continuing example](../assets/calibration/new-29.png)

Study relative scale, reading order, native labels, and selective emphasis. Do not duplicate the pages or facts. Use assets from the current source, with editable text, tables, labels, and annotations.

## Do not learn incidental defects or restrictions

- New's contents still names the old Panoptic chapter. Synchronize navigation after restructuring.
- Both decks contain “Few-label fine-tuning (Zero-shot)”. Keep these settings distinct.
- Some retained notes oversimplify dataset protocols and equation symbols. Recheck sources after edits.
- New 24 shortened notes by removing an old English/source block. Learn the concise narration, but keep citations available in a separate provenance block.
- An added rationale is not automatically a demonstrated finding. Verify it or identify it as inference.
- Do not copy tiny source text, accidental overflow, excessive highlighting, or distorted crops.
- Do not automatically add journal rankings, publication metadata, an architecture survey, or 35 pages. Include only what serves the new brief; verify time-sensitive bibliometrics if used.
- Do not hardcode the omission of Horse-10 or focus on SA-Q/iRodent. Choose scope and representative evidence afresh.

## Acceptance questions

Can this deck be built from the source without a user-written outline? Are prerequisites explained before use? Does a concrete example close any causal gap? Are stages and result conditions visible? Can the audience read comparisons without doing all the arithmetic? Does the PPT follow the current user's chosen template while making the new subject understandable?

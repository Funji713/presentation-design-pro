# Presentation Design Pro

Designs evidence-led, decision-oriented presentation systems before production. It supports executive, sales, product, research, thesis, investor, training, and redesign work where audience, narrative, evidence, charts, accessibility, and production route require deliberate design.

## Presentation template

This repository does not include a default presentation template. Please provide or select your own PowerPoint template, or explicitly configure an accessible local template before requesting template-specific slide production. The SyDog-Video deck below is a finished example, not a default template. Respect the license and attribution requirements of the template you select.

## Example: SyDog-Video

- [Editable 31-slide PowerPoint](examples/sydog-video/SyDog-Video.pptx)
- [Slide architecture and speaker notes](examples/sydog-video/SyDog-Video_outline.md)

This Traditional Chinese research presentation demonstrates source-grounded narrative, editable tables, and a final thank-you slide. Its figures are cropped from Shooter, Malleson and Hilton, *SyDog-Video* (2024), [doi:10.1007/s11263-023-01946-z](https://doi.org/10.1007/s11263-023-01946-z), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The presentation includes the required Slidesgo/Flaticon/Freepik template credits; these credits apply to this example, not to every template.

## Install

Run this in PowerShell to install directly into your local Codex skills directory:

```powershell
git clone https://github.com/Funji713/presentation-design-pro.git "$env:USERPROFILE\.codex\skills\presentation-design-pro"
```

To update an existing installation:

```powershell
git -C "$env:USERPROFILE\.codex\skills\presentation-design-pro" pull --ff-only
```

Start a new Codex task after installation if the current task does not discover the skill.

## Use

```text
$presentation-design-pro Design a 12-slide thesis defense deck from this paper for a 15-minute presentation.
```

The skill establishes the audience, decision goal, narrative, slide architecture, visual system, evidence plan, and production route before creating slides.

See [SKILL.md](SKILL.md) for the full workflow.

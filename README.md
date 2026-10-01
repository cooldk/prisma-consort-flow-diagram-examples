# PRISMA 2020 and CONSORT 2025 flow diagram examples (with count checks)

Worked flow diagram examples for the two most common reporting guidelines — **PRISMA 2020** (systematic reviews) and **CONSORT 2025** (randomised trials) — as editable text (Mermaid), the SVG/PNG files exported from that text, and the numbers in each box as JSON together with the result of a count closure check.

Made with [diagramgen.app](https://diagramgen.app/) — maintained by the diagramgen.app team.

This repository is **not affiliated with or endorsed by the PRISMA or CONSORT groups**. The diagrams do not replace the PRISMA 2020 checklist (27 items) or the CONSORT 2025 checklist (30 items). All counts in the examples are invented for illustration; they are not from a real review or trial.

## What is here

| Example | Variant | Files |
|---|---|---|
| `prisma-2020-new-review` | New review, databases and registers (official template 1 of 4) | `.mmd` `.svg` `.png` `.json` |
| `prisma-2020-new-review-other-sources` | New review, databases + registers + other sources (official template 2 of 4) | `.mmd` `.svg` `.json` |
| `prisma-2020-updated-review` | Updated review, databases and registers (official template 3 of 4) | `.mmd` `.svg` `.json` |
| `prisma-2020-updated-review-other-sources` | Updated review + other sources (official template 4 of 4) | `.mmd` `.svg` `.json` |
| `prisma-2020-new-review-meta-analysis-box` | New review with an extra "studies included in meta-analysis" box — **not** part of any official template | `.mmd` `.svg` `.json` |
| `prisma-2020-blank` | Blank new-review template, counts left as `(n = )` | `.mmd` `.svg` `.json` |
| `consort-2025-two-arm` | Two-arm parallel-group trial | `.mmd` `.svg` `.png` `.json` |
| `consort-2025-three-arm` | Three arms, one box per phase per arm | `.mmd` `.svg` `.json` |
| `consort-2025-blank` | Blank two-arm template | `.mmd` `.svg` `.json` |

- `.mmd` — the diagram as Mermaid text. Edit a number, re-render.
- `.svg` / `.png` — exported on 1 October 2026 with the SVG and PNG buttons of the generator pages below, not edited afterwards. The SVG has every label as real text (no HTML `foreignObject`), so it also renders outside a browser; the PNG is 2× the diagram size on a white background.
- `.json` — every box with its counts (and breakdowns), plus the closure check: each rule, the calculation, and whether it adds up.

[`RULES.md`](RULES.md) lists the closure rules and where they come from.

## Reproduce an example in the tool

1. Open the generator: PRISMA — <https://diagramgen.app/prisma-flow-diagram-generator/>, CONSORT — <https://diagramgen.app/consort-flow-diagram-generator/>.
2. Paste the contents of a `.mmd` file into the **Source** box (or pick the matching template under *Load example*).
3. The diagram renders in your browser; the **Count check** under the preview shows the same rules as the `.json` file. Change a count and the check names the box that no longer adds up. It is a warning only — rendering and export are never blocked.
4. Export with **SVG** or **PNG**. Nothing is uploaded: rendering, checking and exporting all happen in the browser.

For LaTeX, the SVG can be converted to a vector PDF with librsvg (tested on 1 October 2026 with librsvg 2.62; text stays selectable):

```sh
rsvg-convert -f pdf -o prisma.pdf prisma-2020-new-review.svg
```

Not tested by us: Microsoft Word, Overleaf, or specific journal submission systems.

## Limits worth knowing

- The count check is arithmetic on the numbers in the text. It cannot tell whether the numbers are right, and it reads the boxes by the template ids (`A`, `B`, `C` … for PRISMA; `A`, `X`, `R`, `B1`, `C1`, `D1` … for CONSORT). Rename the ids and the check switches off.
- Two counts in one box are separated by a semicolon (`Studies included in review (n = 38); reports of included studies (n = 42)`); a total with a breakdown uses a colon (`Excluded (n = 172): not meeting inclusion criteria (n = 118), …`).
- Layout is automatic (Mermaid). Boxes, wording and arrows follow the official templates; positions can differ from the official figures.
- Labels wrap at about 200 px, so long reason lists make boxes taller.
- CONSORT designs with their own extension (cluster, crossover, factorial, non-inferiority, multi-arm …) may need more boxes than the standard diagram drawn here.

## Sources

- Page MJ, McKenzie JE, Bossuyt PM, et al. The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. *BMJ* 2021;372:n71. doi:[10.1136/bmj.n71](https://doi.org/10.1136/bmj.n71)
- PRISMA 2020 flow diagram templates (four variants), prisma-statement.org: <https://www.prisma-statement.org/prisma-2020-flow-diagram> — box wording compared on 1 October 2026. The templates are distributed under CC BY 4.0.
- Hopewell S, Chan AW, Collins GS, et al. CONSORT 2025 statement: updated guideline for reporting randomised trials. *BMJ* 2025;389:e081123 (published 14 April 2025). doi:[10.1136/bmj-2024-081123](https://doi.org/10.1136/bmj-2024-081123). Note: the footer of the CONSORT 2025 flow diagram Word template on consort-spirit.org cites volume 388; PubMed and Europe PMC list volume 389.
- CONSORT 2025 flow diagram template, consort-spirit.org: <https://www.consort-spirit.org/> — box wording compared on 1 October 2026.

## Licence

The example diagrams, Mermaid sources, exported images and JSON files in this repository are licensed under [CC BY 4.0](LICENSE). Box wording is adapted from the PRISMA 2020 flow diagram templates and the CONSORT 2025 flow diagram, both published under CC BY 4.0 — cite the statements above when you use them.

Suggested attribution: *"Flow diagram example adapted from diagramgen.app PRISMA/CONSORT examples (CC BY 4.0); template wording from PRISMA 2020 (Page et al., BMJ 2021) / CONSORT 2025 (Hopewell et al., BMJ 2025)."*

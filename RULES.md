# Closure rules

The rules the count check applies — the same code runs in the browser on diagramgen.app and produced the `closure` block in every `examples/*.json`. Each rule is attached to box ids, not to wording, so it works in every language the templates are offered in.

Two kinds of rule:

- **hard** — follows from the definitions of the boxes; if it does not hold, a number is wrong.
- **soft** — usually holds, but there are legitimate exceptions; a mismatch is shown as "usually equal — explain any difference in your text".

## PRISMA 2020

Source: Page MJ et al. *BMJ* 2021;372:n71 (doi:10.1136/bmj.n71) and the four official flow diagram templates on prisma-statement.org (compared 1 October 2026). The statement defines a *record* as the title or abstract of a report indexed in a database or website, a *report* as a document supplying information about a study, and notes that a study might have several reports.

| Rule | Kind | Boxes |
|---|---|---|
| Records screened = records identified − records removed before screening | hard | C = A − B |
| Reports sought for retrieval = records screened − records excluded | **soft** (one record can lead to more than one report) | E = C − D |
| Reports assessed for eligibility = reports sought − reports not retrieved | hard | G = E − F |
| Other methods column: reports assessed = reports sought − reports not retrieved | hard | N = L − M |
| Reports of included studies = (reports assessed − reports excluded) [+ the same for the other-methods column] | hard | I(reports) = (G − H) [+ (N − O)] |
| Studies included ≤ reports of included studies (every study has at least one report) | hard | I(studies) ≤ I(reports) |
| Updated review: total studies = previous studies + new studies; same for reports | hard | T = P + I |
| Studies in an added meta-analysis box ≤ studies included | hard | J ≤ I(studies) |
| A total with a breakdown equals the sum of its parts (e.g. records removed: duplicates + automation + other) | hard | any box written as `Total (n = …): part (n = …), part (n = …)` |

If the included box carries only one count, the check can only assert *studies included ≤ reports assessed − reports excluded*.

The official templates also ask, where feasible, for records per database or register, and — if automation tools excluded records — how many were excluded by a human and how many by the tools. Write those as parts of the box (`Records identified from: MEDLINE (n = 512), Embase (n = 668), registers (n = 60)`); the check adds them up.

## CONSORT 2025

Source: Hopewell S et al. *BMJ* 2025;389:e081123 (doi:10.1136/bmj-2024-081123) and the CONSORT 2025 flow diagram template from consort-spirit.org (compared 1 October 2026). Arms are read as `B1`…`B9` (allocation), `C1`… (follow-up), `D1`… (analysis).

| Rule | Kind | Boxes |
|---|---|---|
| Randomised = assessed for eligibility − excluded | hard | R = A − X |
| Excluded = not meeting inclusion criteria + declined to participate + other reasons | hard | X = sum of its parts |
| The arms add up to randomised | hard | R = B1 + B2 (+ B3 …) |
| In each arm, allocated = received allocated intervention + did not receive it | hard | Bk = sum of its parts |
| Analysed for primary outcome = allocated − lost to follow-up for primary outcome − excluded from analysis | **soft** (with imputed outcomes, analysed can equal allocated) | Dk(analysed) = Bk − Ck(lost) − Dk(excluded) |

Participants who discontinued the intervention can still be followed up and analysed, so "discontinued" is not subtracted anywhere.

## What the check does not do

It does not verify that counts are correct, that exclusion reasons are complete, or that a report meets the PRISMA 2020 or CONSORT 2025 checklist. It only checks that the numbers written in the diagram are consistent with each other.

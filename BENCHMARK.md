# Benchmark: USM Harvard Citation Skill

This benchmark measures how well Claude follows the Harvard-USM Ver 2020 style **with** the skill and **without** it. The model, prompt and references are the same in both conditions. Scoring was automatic, by a script that checks each rule.

## Results at a glance

| Test set | With skill | Without skill |
|---|---|---|
| Main set: 17 references and 6 in-text citations, 53 checks | **100%** (159/159) | 72% (115/159) |
| Held-out set: 9 new references and 4 in-text citations, 30 checks | **98%** (88/90) | 61% (55/90) |

Each condition was run 3 times on each set. Model: Claude Opus 5.5 (`claude-opus-5-5`), headless Claude Code 2.1.309, run on 23 October 2026.

## What was tested

**Main set.** These are real references:
- 12 come from the EndNote Harvard-USM output in a USM MPH research report (GKT517, 2024). They include errors EndNote produced: `doi:` prefixes, `Proceedings from Proceedings`, `(eds.)`, `pp` with no full stop, and missing pages.
- 5 are PubMed articles in Vancouver style. They cover article numbers, a journal with no issue numbers, a supplement issue, 13 authors and 90 authors.

These cases were used while the skill was being built, so the skill was tuned on them.

**Held-out set.** This set holds 9 references the skill was **not** built or tuned on:
- PubMed articles, a textbook, a WHO webpage, and a book chapter.
- One entry from the MPH report with `et al.` and a missing DOI.
- They are given in APA 7 and Vancouver styles, which the skill had not been tested on.

This set shows how the skill handles new input.

**In-text citations** were tested in both sets: `&` vs `and`, `et al.`, several sources sorted by year, organisation abbreviations, secondary sources, same author and year (`2019a`), and sources with no author.

## Method

1. Both conditions get the same prompt. The prompt asks for USM Harvard, says to mark missing information as `[MISSING: field]`, and sets a fixed output block so the answer can be scored.
2. **With skill:** the prompt starts with "Use the usm-harvard-citation skill" and the skill is installed.
3. **Without skill:** skills are turned off (`--disable-slash-commands`), and no file or web tools are available. Claude relies only on what it already knows about "USM Harvard".
4. A scoring script checks each output against a fixed list of rules. Each check is one rule on one entry, for example "volume and issue in bold: **36(1)**". A check passes or fails, with no partial marks.

## What the results show

- **Without the skill, Claude writes general UK Harvard (Cite Them Right), not Harvard-USM.** It used `and` instead of `&` between authors, `Available at:` instead of `Retrieved from:`, and `3rd ed.` without brackets. It also kept the `doi:` prefix, and no run put volume and issue in bold.
- **The largest gains are USM-specific rules:**
  - font styles: bold volume and issue, from 25-50% to 100%;
  - book chapters: `(Eds.)` and editors joined with `and`;
  - online theses formatted like webpages;
  - `Proceedings from`;
  - 21+ authors as first 19, `...`, last author;
  - secondary sources as `as cited in`;
  - in-text `&` and `2019a`.
- **Both conditions marked missing data and did not invent it.** The prompt itself told Claude to mark missing information, so this benchmark does not show whether the skill improves honesty. It shows how well Claude knows the style.

## Where the skill failed

| Check | Result | What happened |
|---|---|---|
| H06: BMC Emergency Medicine `14, 17` | 1/3 runs passed | In 2 runs the skill wrote `**14([MISSING: issue])**, 17`. BMC journals publish by volume and article number, so the issue should not be marked as missing. The source is not wrong, but the skill raised a false alarm. |

## Limits of this benchmark

- The main set was used during development, so its 100% score is optimistic. The held-out score (98%) is the better guide to performance on new references.
- The sets are small: 26 references and 83 checks. Three runs per condition shows some variation between runs, but not a full statistical picture.
- Only one model (Opus 5.5) was tested. Smaller models may score lower.
- The checks test the rules in this skill, which come from the lecture slides and the EndNote style. Where the IPS guideline differs, the IPS guideline wins.
- The scorer checks text patterns. It does not check that a DOI or URL leads to the right source.

## Full results

The tables below list every check and how many of the 3 runs passed it.

### Set: main (53 checks, 3 runs each)

| | With skill | No skill |
|---|---|---|
| Checks passed (all runs) | 159/159 (100%) | 115/159 (72%) |
| Score per run | 53, 53, 53 | 38, 38, 39 |

| Category | Checks | With skill | No skill |
|---|---|---|---|
| DOI | 4 | 100% | 50% |
| Missing data | 7 | 100% | 100% |
| No invention | 2 | 100% | 100% |
| Journal | 6 | 100% | 89% |
| Web | 2 | 100% | 100% |
| Thesis | 1 | 100% | 0% |
| Authors | 9 | 100% | 78% |
| Font | 8 | 100% | 50% |
| Conference | 2 | 100% | 50% |
| Chapter | 4 | 100% | 50% |
| List | 2 | 100% | 100% |
| In-text | 6 | 100% | 67% |

| ID | Category | Check | With skill | No skill |
|---|---|---|---|---|
| R01 | DOI | DOI as https://doi.org link, no doi: prefix | 3/3 | 0/3 |
| R02 | DOI | No full stop after the DOI | 3/3 | 3/3 |
| R03 | Missing data | Missing pages marked | 3/3 | 3/3 |
| R04 | No invention | Page not taken from the DOI (14) | 3/3 | 3/3 |
| R05 | Journal | Article number 61 kept in place of pages, not flagged | 3/3 | 3/3 |
| R06 | Web | Retrieved from: with a space | 3/3 | 3/3 |
| R07 | Thesis | Online thesis as webpage: no degree, institution or MISSING added | 3/3 | 0/3 |
| R08 | Authors | Vancouver authors converted: Borges, G. & Orozco, R. (2023) | 3/3 | 3/3 |
| R09 | Journal | Volume(issue), pages: 29(3), 207-212 | 3/3 | 3/3 |
| R10 | Font | Volume and issue in bold: **29(3)** | 3/3 | 0/3 |
| R11 | Font | Journal name in italics | 3/3 | 3/3 |
| R12 | Missing data | Missing article number marked | 3/3 | 3/3 |
| R13 | No invention | Article number not taken from the DOI | 3/3 | 3/3 |
| R14 | Conference | No repeated 'Proceedings from Proceedings' | 3/3 | 3/3 |
| R15 | Conference | Uses 'Proceedings from' | 3/3 | 0/3 |
| R16 | Missing data | Missing pages marked | 3/3 | 3/3 |
| R17 | Missing data | Missing publisher marked | 3/3 | 3/3 |
| R18 | DOI | http:// DOI changed to https://doi.org | 3/3 | 3/3 |
| R19 | Authors | Organisation abbreviation DOSH kept as author, as in the source | 3/3 | 0/3 |
| R20 | Web | Retrieved from: with a space | 3/3 | 3/3 |
| R21 | Authors | Author fixed to Dressner, M. A. | 3/3 | 3/3 |
| R22 | Missing data | Missing volume marked | 3/3 | 3/3 |
| R23 | Missing data | Missing pages marked | 3/3 | 3/3 |
| R24 | Font | Journal name in italics | 3/3 | 3/3 |
| R25 | Font | Volume and issue in bold: **36(1)** | 3/3 | 0/3 |
| R26 | Font | Pages not bold | 3/3 | 0/3 |
| R27 | Font | Volume-only journal in bold: **33** | 3/3 | 0/3 |
| R28 | Chapter | (eds.) changed to (Eds.) | 3/3 | 0/3 |
| R29 | Chapter | pp changed to pp. | 3/3 | 3/3 |
| R30 | Chapter | Editors joined with 'and', as in the slides | 3/3 | 0/3 |
| R31 | Font | Book title in italics | 3/3 | 3/3 |
| R32 | Chapter | Pages after the publisher | 3/3 | 3/3 |
| R33 | Authors | All 13 authors listed, no et al. | 3/3 | 3/3 |
| R34 | Authors | Multiple initials converted: Job, R. F. S. | 3/3 | 3/3 |
| R35 | Font | Book title in italics | 3/3 | 3/3 |
| R36 | Missing data | Missing place of publication marked | 3/3 | 3/3 |
| R37 | Authors | Authors converted with & before the last | 3/3 | 3/3 |
| R38 | Journal | Article number 1149 kept, not flagged | 3/3 | 3/3 |
| R39 | Authors | 21+ authors: first 19, ..., last author | 3/3 | 0/3 |
| R40 | Journal | Supplement written as Suppl. 1 | 3/3 | 1/3 |
| R41 | Authors | No et al. in the reference list | 3/3 | 3/3 |
| R42 | Journal | Volume-only journal not flagged: 128, 159-163 | 3/3 | 3/3 |
| R43 | Authors | Vancouver author converted: Mohan, D. (2019) | 3/3 | 3/3 |
| G1 | List | All 17 entries present | 3/3 | 3/3 |
| G2 | List | Alphabetical order | 3/3 | 3/3 |
| G3 | DOI | No doi: prefix anywhere | 3/3 | 0/3 |
| G4 | Journal | No space in volume(issue), e.g. 62(3) | 3/3 | 3/3 |
| T1 | In-text | Two authors in brackets use & | 3/3 | 2/3 |
| T2 | In-text | Two authors in a sentence use and | 3/3 | 3/3 |
| T3 | In-text | Three or more authors use et al. | 3/3 | 3/3 |
| T4 | In-text | Several sources sorted by year, separated by ; | 3/3 | 1/3 |
| T5 | In-text | Organisation abbreviation | 3/3 | 3/3 |
| T6 | In-text | Secondary source | 3/3 | 0/3 |

### Set: holdout (30 checks, 3 runs each)

| | With skill | No skill |
|---|---|---|
| Checks passed (all runs) | 88/90 (98%) | 55/90 (61%) |
| Score per run | 29, 30, 29 | 18, 20, 17 |

| Category | Checks | With skill | No skill |
|---|---|---|---|
| Authors | 2 | 100% | 33% |
| Font | 4 | 100% | 25% |
| Journal | 6 | 89% | 89% |
| DOI | 2 | 100% | 100% |
| Book | 1 | 100% | 0% |
| Missing data | 4 | 100% | 75% |
| Web | 2 | 100% | 50% |
| Chapter | 2 | 100% | 50% |
| No invention | 1 | 100% | 100% |
| List | 2 | 100% | 100% |
| In-text | 4 | 100% | 33% |

| ID | Category | Check | With skill | No skill |
|---|---|---|---|---|
| H01 | Authors | APA comma before & removed: Haque, M. S. & Sadhra | 3/3 | 1/3 |
| H02 | Font | Volume and issue in bold: **69(2)** | 3/3 | 0/3 |
| H03 | Journal | Pages kept: 99-105 | 3/3 | 2/3 |
| H04 | Authors | Vancouver authors converted with & before the last | 3/3 | 1/3 |
| H05 | DOI | doi: converted to https://doi.org link | 3/3 | 3/3 |
| H06 | Journal | Article number 17 kept in place of pages | 1/3 | 3/3 |
| H07 | Journal | APA 'Article 6641' written as the article number only | 3/3 | 3/3 |
| H08 | Font | Volume and issue in bold: **19(11)** | 3/3 | 0/3 |
| H09 | Book | Edition kept: (3rd ed.) | 3/3 | 0/3 |
| H10 | Font | Book title in italics | 3/3 | 3/3 |
| H11 | Missing data | Missing place of publication marked (APA 7 leaves it out) | 3/3 | 3/3 |
| H12 | Journal | Article title changed to sentence case | 3/3 | 3/3 |
| H13 | Font | Volume and issue in bold: **23(4)** | 3/3 | 0/3 |
| H14 | Web | Retrieved from: URL | 3/3 | 0/3 |
| H15 | Missing data | Missing access date marked | 3/3 | 3/3 |
| H16 | Web | Year only in brackets: (2023) | 3/3 | 3/3 |
| H17 | Chapter | APA 'In B. Mondal & G. Samanta (Eds.)' converted to 'In: Mondal, B. and Samanta, G. (Eds.)' | 3/3 | 0/3 |
| H18 | Chapter | Pages as pp. 131-147 after the publisher | 3/3 | 3/3 |
| H19 | Missing data | Missing place of publication marked | 3/3 | 3/3 |
| H20 | No invention | et al. removed and missing authors marked, not guessed | 3/3 | 3/3 |
| H21 | Journal | Space removed: 10(4) | 3/3 | 2/3 |
| H22 | Missing data | Missing DOI or URL marked | 3/3 | 0/3 |
| H23 | Journal | e-page kept: 16(7), e64445 | 3/3 | 3/3 |
| G1 | List | All 9 entries present | 3/3 | 3/3 |
| G2 | List | Alphabetical order | 3/3 | 3/3 |
| G3 | DOI | No doi: prefix anywhere | 3/3 | 3/3 |
| T1 | In-text | Three authors in a sentence use et al. | 3/3 | 1/3 |
| T2 | In-text | Same authors, same year: add a | 3/3 | 0/3 |
| T3 | In-text | Several sources sorted by year | 3/3 | 1/3 |
| T4 | In-text | No author: title in double quotes | 3/3 | 2/3 |

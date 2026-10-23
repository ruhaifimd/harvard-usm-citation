# USM Harvard Citation Skill (Harvard-USM Ver 2020)

A Claude skill for formatting, checking, and correcting in-text citations and reference lists in the USM Harvard style. It is for theses, dissertations, and academic writing at Universiti Sains Malaysia (USM), following the IPS writing guideline.

**Based on:** APA 6th Edition (author-date), with the USM-specific rules from the Harvard-USM Ver 2020 EndNote style.

## What It Does

- **Formats in-text citations:** 1 author, 2 authors, 3+ authors (`et al.`), same author same year (a, b, c), several sources, no author, organisation as author, secondary sources, personal communication.
- **Formats reference-list entries** for journal articles, books, book chapters, conference papers, theses (print and online), reports, computer programmes, webpages, and translated or reprinted works.
- **Checks and corrects** an existing reference list: order, `&` vs `and`, `et al.` in the list, DOI format, `62(3)` volume format, and `Anonymous`.
- **Marks missing information in red** (for example `[MISSING: pages]`). It never invents a DOI, page number, publisher, or degree type.

## Supported Source Types

Journal articles (with and without DOI) · Books · Book chapters (edited books) · Conference papers and proceedings · Theses and dissertations (print, online, unpublished) · Reports · Computer programmes · Webpages and electronic sources · Translated works · Reprinted works · Personal communication · Secondary sources

## Installation

1. Download or clone this repo.
2. Copy the folder `skill/usm-harvard-citation` into your Claude skills folder:
   - **Claude Code:** `~/.claude/skills/usm-harvard-citation/`
   - **Other Claude apps:** upload the `usm-harvard-citation` folder through the skills settings, if your app supports custom skills.
3. Start a new session.

## How to Use

Ask Claude in plain language. For example:

- "Format this in USM Harvard: Smith J, Ali B. 2013. Vaccine uptake in Kelantan. Med J Malaysia 68(2):45-50"
- "Check this reference list for USM Harvard: ..."
- "Cite this URL in USM Harvard: https://..."
- "Convert this APA reference to USM Harvard: ..."
- "Sort my reference list and show me what changed."

## Example (fictitious)

Input: `Smith J, Ali B. 2013. Vaccine uptake in Kelantan. Med J Malaysia 68(2):45-50`

In-text citation: `(Smith & Ali, 2013)`

Reference list entry: `Smith, J. & Ali, B. (2013). Vaccine uptake in Kelantan. Med J Malaysia, 68(2), 45-50.`

## Benchmark

The same model was given the same references with and without the skill, and the outputs were scored automatically against the Harvard-USM rules. Each condition ran 3 times.

| Test set | With skill | Without skill |
|---|---|---|
| Main set: 17 references and 6 in-text citations from a USM MPH report and PubMed, 53 checks | **100%** | 72% |
| Held-out set: 9 new references in APA 7 and Vancouver, not used to build the skill, 30 checks | **98%** | 61% |

Without the skill, Claude writes general UK Harvard instead of Harvard-USM. The skill adds the USM rules it does not know: bold volume and issue, `&` between authors, `Retrieved from:`, `(Eds.)`, `Proceedings from`, online theses, and 21+ authors. The one failure on the held-out set was a false alarm, a missing issue marked for a BMC journal. Model: Claude Opus 5.5, October 2026.

Method, limits and every check are in [BENCHMARK.md](BENCHMARK.md).

## File Structure

```
harvard-usm-citation/
├── README.md
├── BENCHMARK.md                                  # Benchmark method and results
├── LICENSE
└── skill/
    └── usm-harvard-citation/
        ├── SKILL.md                              # Main skill instructions
        └── references/
            ├── usm-formatting-rules.md           # Templates and rules for each source type
            └── examples.md                       # Worked examples, including missing-field cases
```

Only the `skill/usm-harvard-citation` folder needs to be installed.

## Sources

- Lecture slides "Referencing" by Assoc. Prof. Dr WM Zahiruddin Wan Mohammad, School of Medical Sciences, USM (MPH GKT517, 2023/2024).
- EndNote style "Harvard-USM Ver 2020", by Assoc. Prof. Dr Wan Mohd Zahiruddin (SMS) and Nurul Azurah Mohd Roni (Library), USM.
- Manual for Harvard USM Version 2020 (pustaka.kk.usm.my).
- IPS USM, *A Guide to the Preparation, Submission and Examination of Thesis* (writing style, pages 8-10).

The EndNote style file itself is not included in this repo. To use it in EndNote, get it from the USM library or from the authors.

## Limits

- The skill formats citations. It does not check that a source exists. Verify every DOI and URL before you submit.
- The EndNote style file (`.ens`) is a binary format. The rules here come from the slides and the style's own text. For an exact check, use EndNote's Output Styles Editor.
- If the IPS guideline and this skill disagree, follow the IPS guideline.

## Licence

MIT. See [LICENSE](LICENSE). The style rules belong to the authors named above, who are credited here.

## Feedback

Please report errors or missing source types by opening an issue.

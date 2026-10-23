# USM Harvard Citation Skill (Harvard-USM Ver 2020)

A Claude skill that formats in-text citations and reference lists in the USM Harvard style, for theses, dissertations and academic writing at Universiti Sains Malaysia.

> **Status:** draft. Not yet tested on real references.

## What it does

- Formats in-text citations (1 author, 2 authors, 3+ authors, same author same year, several sources, no author, secondary sources).
- Formats reference-list entries for journal articles, books, book chapters, conference papers, theses, reports, computer programmes, and websites or online sources.
- Checks a reference list for missing fields, wrong order, and "Anonymous".

## Install

Copy the folder `skill/usm-harvard-citation` into your Claude skills folder (for Claude Code: `~/.claude/skills/`), then start a new session.

## Example

Input: `Smith J, Ali B. 2013. Vaccine uptake in Kelantan. Med J Malaysia 68(2):45-50`

Output in-text: `(Smith & Ali, 2013)`

Output reference: `Smith, J. & Ali, B. (2013). Vaccine uptake in Kelantan. Med J Malaysia, 68(2), 45-50.`

## Sources

- Lecture slides "Referencing" by Assoc. Prof. Dr WM Zahiruddin Wan Mohammad, School of Medical Sciences, USM (MPH GKT517, 2023/2024).
- EndNote style "Harvard-USM Ver 2020", by Assoc. Prof. Dr Wan Mohd Zahiruddin (SMS) and Nurul Azurah Mohd Roni (Library), USM.
- Manual for Harvard USM Version 2020 (pustaka.kk.usm.my).
- IPS USM, *A Guide to the Preparation, Submission and Examination of Thesis* (writing style, pages 8-10).

The style file itself is not included in this repo. To use it in EndNote, get it from the USM library or from the authors.

## Limits

- The skill formats citations. It does not check that a source exists. Verify every DOI and URL before you submit.
- The EndNote style file (`.ens`) is a binary format. The rules here come from the slides and the style's own text. For an exact check, use EndNote's Output Styles Editor.
- If the IPS guideline and this skill disagree, follow the IPS guideline.

## Licence

MIT. See [LICENSE](LICENSE). The style rules belong to the authors named above, who are credited here.

## Feedback

Please report errors or missing types by opening an issue.

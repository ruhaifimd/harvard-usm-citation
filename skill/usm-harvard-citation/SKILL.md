---
name: usm-harvard-citation
description: Format in-text citations and reference lists in the USM Harvard style (Harvard-USM Ver 2020, based on APA 6th). Use when the user asks to cite a source, format references, build a bibliography, check citations in a USM thesis, dissertation, or article, or convert references to USM Harvard style.
---

# USM Harvard Citation (Harvard-USM Ver 2020)

This skill formats citations for USM theses, dissertations and academic writing that follow the USM Institute of Postgraduate Studies (IPS) guideline. The style is Harvard (author-date) based on APA 6th edition, with USM-specific punctuation and types.

Source of the rules: the "Referencing" lecture slides by Assoc. Prof. Dr WM Zahiruddin Wan Mohammad (MPH GKT517, USM 2023/2024), and the EndNote style "Harvard-USM Ver 2020" by Assoc. Prof. Dr Wan Mohd Zahiruddin (SMS) and Nurul Azurah Mohd Roni (Library). If the user's rule conflicts with the IPS guideline, follow the IPS guideline and say so.

## Step 1: Gather the metadata

Before formatting, check you have the fields needed for the source type (see `references/examples.md`). Required for most types: author(s), year, title, and either a DOI or URL. If a field is missing, never invent it. Write the missing part in **red** so the author cannot miss it, using this exact form:

`<span style="color:red">**[MISSING: field name]**</span>`

If the output cannot show HTML colour, write `**[MISSING: field name]**` and say in your reply that these must be shown in red. Never invent a DOI, page number, publisher, issue number or degree type.

## Step 2: In-text citation

**Placement.** Put the citation where the idea appears. Usually before the full stop:
- Outside the sentence: `(Smith, 2013)`
- Inside the sentence: `Smith (2013) described that...`

**Number of authors:**
- 1 author: `(Smith, 2013)`
- 2 authors, outside sentence: `(Zahiruddin & Naing, 2002)`
- 2 authors, inside sentence: `Zahiruddin and Naing (2002) described that...`
- 3 or more authors: first author + `et al.`, italic in the text: `(Wilson et al., 1997)` or `Wilson et al. (1997)`

**Same author, same year:** add a, b, c after the year: `(Johnson, 1994a)`, `(Johnson, 1994b)`. The letters follow the order in the reference list.

**Several sources in one bracket:** sort by year and separate with a semicolon: `(Smith, 1999; Jones et al., 2001; Turner & William, 2006)`.

**No personal author:**
- Use the organisation: `(WHO, 2013)`
- If there is no author at all, use the first few words of the title in double quotes plus the year: `("New Child Vaccine," 2001)`
- Do not use "Anonymous".

**Personal communication** (letter, interview, email, lecture): cite in text only, not in the reference list, for example `(J. D. Black, personal communication, May 30, 2013)`. Recommend avoiding it.

**Secondary source** (you did not read the original): cite both: `(Miller, 1953, as cited in Agrios, 2005)`. Only the source you read goes in the reference list.

## Step 3: Reference list

- Title: `References`. Sort alphabetically by first author's surname. Use a hanging indent in Word.
- Use sentence case for article and book titles.
- Authors: `Surname, Initials.` separated by commas, with `&` before the last author.
- Year in round brackets after the authors.
- DOI always as a clickable link: `https://doi.org/10.xxxx/xxxxx`. Do not write the `doi:` prefix. If the source gives `doi: https://doi.org/...`, convert it to `https://doi.org/...`. If there is no DOI, use the URL.
- Journal volume and issue with no space: `62(3)`, not `62 (3)`.
- Between 2 and 20 authors: list all authors.
- 21 or more authors: list the first 19, then `...`, then the last author. EndNote does not do this automatically, so edit the entry by hand.

### Templates by type

**Journal article**
`Surname, A. B., Surname, C. D. & Surname, E. (Year). Article title in sentence case. Journal Name, Volume(Issue), pages. https://doi.org/xx`

If pages or issue are missing, write them in red as `**[MISSING: pages]**` or `**[MISSING: issue]**`. A journal article number (for example `14` in `mjmhs.19.3.14`) is not a page range. Ask the author for the page range.

**Book**
`Surname, A. B. & Surname, C. (Year). Book title (2nd ed.). Place: Publisher.`
Leave out the edition if it is the first edition.

**Book chapter**
`Surname, A. B. (Year). Chapter title. In: Editor Surname, A. B. (Ed.), Book title (pp. xx-xx). Place: Publisher.`
For 2 editors use `(Eds.)`.

**Conference paper / proceedings**
`Surname, A. B. (Year). Paper title. In: Conference name (pp. xx-xx). Place: Publisher.`

**Thesis or dissertation**
`Surname, A. B. (Year). Title of thesis (Dissertation). Institution name, Place.`
Unpublished student dissertation: `(Unpublished work)` instead of `(Dissertation)`.

**Thesis found online** (repository or e-print link):
`Surname, A. B. (Year). Title of thesis (Dissertation). Institution name. Retrieved from URL [Accessed dd Month yyyy].`
- The institution can be read from the URL (for example `uum.edu.my` is Universiti Utara Malaysia), but say so. Mark the institution in red if you inferred it: `<span style="color:red">**[CHECK: institution inferred from URL]**</span>`.
- The degree (Master's or PhD) is not in the URL. Write `(Dissertation)` and mark it in red: `<span style="color:red">**[MISSING: degree type]**</span>`.
- Write `Retrieved from URL` with a space after the colon, even if the source does not have one.

**Report**
`Organisation. (Year). Report title (Report No. xx). Place: Publisher.`

**Computer programme**
`Surname, A. B. (Year). Program name (Version x.x) [Computer software]. Publisher.`

**Website or electronic source**
`Organisation or Author. (Year). Page title. Retrieved from URL [Accessed dd Month yyyy].`
Note that the USM style writes `Retrieved from` and `[Accessed ...]`.

**Translated work:** `Surname, A. B. (Year). Title (C. D. Translator, Trans.). Place: Publisher.`

**Reprinted work:** add `(Reprinted from: ...)` after the title.

## Step 4: Check the output

Before returning the result, check:
1. Every in-text citation has a matching reference-list entry, and every reference-list entry is cited in the text (except personal communications and secondary sources listed as "as cited in").
2. Same-author same-year items have a, b, c.
3. The list is in alphabetical order.
4. No `Anonymous`, no invented DOI, no missing year. Every missing or uncertain field is in red, and the reply lists them.
5. Italics are used for journal names, book titles, and `et al.` in text. Say that the user should apply italics in Word, since plain text cannot show them.

## Output format

When the user gives a source, return:
1. The in-text citation.
2. The reference-list entry.
3. A list of anything missing or uncertain.

When the user gives a whole reference list, return the corrected list in alphabetical order, and list each change made.

## Limits

- The EndNote style file (`.ens`) is a binary file that was not fully decoded. The rules above come from the lecture slides and the style's own text. If the user needs an exact check for a rule not listed here, tell them to check it in EndNote's Output Styles Editor.
- The skill formats citations. It does not verify that a source exists. Tell the user to check each DOI or URL before submission.

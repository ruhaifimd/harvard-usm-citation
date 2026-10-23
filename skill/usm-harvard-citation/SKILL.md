---
name: usm-harvard-citation
allowed-tools: Read
description: Format, check, and correct in-text citations and reference lists in the USM Harvard style (Harvard-USM Ver 2020, based on APA 6th) for USM theses, dissertations, and academic writing. Use whenever the user asks to format, check, proofread, or fix a citation or reference; build a bibliography; cite a source, URL, or DOI in USM Harvard; convert references to USM Harvard; or pastes a reference list. Trigger on mentions of 'Harvard USM', 'USM Harvard', 'Harvard-USM', 'IPS', 'thesis referencing', 'reference list', 'in-text citation', 'cite this', 'bibliography', or when references are pasted for review.
---

# USM Harvard Citation (Harvard-USM Ver 2020)

**Based on:** APA 6th Edition (author-date), with the USM Institute of Postgraduate Studies (IPS) writing guidelines.
**Sources of rules:**
- Lecture slides "Referencing", Assoc. Prof. Dr WM Zahiruddin Wan Mohammad, School of Medical Sciences, USM (MPH GKT517, 2023/2024).
- EndNote style "Harvard-USM Ver 2020", by Assoc. Prof. Dr Wan Mohd Zahiruddin (SMS) and Nurul Azurah Mohd Roni (Library), USM.

If a rule here conflicts with the IPS guideline, follow the IPS guideline and say so.

---

## How to Use This Skill

### Step 1: Identify the task

- **"Format this"**: the user gives source details and wants an in-text citation and a reference-list entry.
- **"Check this"**: the user pastes one or more references and wants them reviewed.
- **"Cite this URL or DOI"**: the user gives a link. Read the metadata first, then format it. Do not guess missing fields.
- **"Convert this"**: the user has references in another style (APA, MLA, Chicago, EndNote output) and wants USM Harvard.
- **Whole reference list**: format or check every entry, then sort the list.

### Step 2: Identify the source type

Find the source type in `references/usm-formatting-rules.md`. That file has the template and an example for each type:

| Category | Types |
|---|---|
| Journals | Article with DOI, article without DOI, online article |
| Books | Book, book chapter (edited book) |
| Conference | Conference paper or proceedings |
| Theses | Thesis or dissertation (print), thesis found online, unpublished student dissertation |
| Reports and software | Report, computer programme |
| Web | Webpage or electronic source, website with no author |
| Other | Translated work, reprinted work, personal communication, secondary source |

### Step 3: Apply the rules

Use `references/usm-formatting-rules.md` for the template. Use the general rules below for in-text citations and the reference list.

### Step 4: Check for missing or uncertain information

- Never invent a DOI, page number, issue number, publisher, degree type, or institution.
- Mark every missing or uncertain field in **red** so the author cannot miss it. Use this exact form:

  `<span style="color:red">**[MISSING: field name]**</span>`

  For a field you inferred but the author must check, use:

  `<span style="color:red">**[CHECK: what was inferred]**</span>`

- If the output cannot display HTML colour, write `**[MISSING: field name]**` and say in your reply that these must be shown in red.

### Step 5: Return the result

Use the output format below. Do not skip the checklist of missing or uncertain fields.

---

## General Rules

### In-text citations

**Placement.** Put the citation where the idea appears. Usually before the full stop.
- Outside the sentence: `(Smith, 2013)`
- Inside the sentence: `Smith (2013) described that...`

**Number of authors:**
- 1 author: `(Smith, 2013)`
- 2 authors, outside the sentence: `(Zahiruddin & Naing, 2002)`
- 2 authors, inside the sentence: `Zahiruddin and Naing (2002) described that...`
- 3 or more authors: first author + `et al.`, in italics in the text: `(Wilson et al., 1997)` or `Wilson et al. (1997)`

**Same author, same year:** add a, b, c after the year: `(Johnson, 1994a)`, `(Johnson, 1994b)`. The letters follow the order in the reference list.

**Several sources in one bracket:** sort by year and separate with a semicolon: `(Smith, 1999; Jones et al., 2001; Turner & William, 2006)`.

**No personal author:**
- Use the organisation: `(WHO, 2013)`
- If there is no author at all, use the first few words of the title in double quotes plus the year: `("New Child Vaccine," 2001)`
- Do not use "Anonymous".

**Personal communication** (letter, interview, email, lecture): in-text only, not in the reference list. Example: `(J. D. Black, personal communication, May 30, 2013)`. Recommend avoiding it.

**Secondary source** (you did not read the original): cite both, for example `(Miller, 1953, as cited in Agrios, 2005)`. Only the source you read goes in the reference list.

### Reference list

- Heading: `References`. Sort alphabetically by the first author's surname.
- Authors: `Surname, Initials.`, separated by commas, with `&` before the last author.
- Year in round brackets after the authors.
- Journal volume and issue with no space: `62(3)`, not `62 (3)`.
- **Article numbers:** many online journals (for example BMC, Sports Medicine - Open) use an article number instead of pages. Write the article number in place of the page range, as in the slide example `Int Breastfeed J, 7(1), 11`. Do not mark it as missing.
- **Supplement issues:** write `Volume(Suppl. N)`, for example `26(Suppl. 1), i46-i56`. Convert `Supp 1`, `Suppl 1` or `S1` to `Suppl. 1`.
- **No issue number:** some journals publish by volume only (for example Accident Analysis & Prevention). If the source gives a volume and pages but no issue, write the volume only, for example `128, 159-163`, and do not mark it. Mark `[CHECK: issue]` only when the journal normally has issues, for example when other articles from the same journal show one.
- **Same markers everywhere:** if an entry has a `[MISSING]` or `[CHECK]` marker, keep the same marker in the final sorted list. Do not drop or change it.
- Journal names as they appear in the source, for example `Med J Malaysia`. Do not change their case.
- Article and book titles in sentence case.
- DOI always as a clickable link: `https://doi.org/10.xxxx/xxxxx`. Do not write the `doi:` prefix. If the source gives `doi: https://doi.org/...`, convert it to `https://doi.org/...`.
- If there is no DOI, use the URL.
- 2 to 20 authors: list all authors.
- 21 or more authors: list the first 19, then `...`, then the last author. EndNote does not do this automatically.
- Do not use `et al.` in the reference list.
- Use hanging indent in Word. Italics for journal names, book titles, and volume numbers. Tell the user to apply italics in Word, since plain text cannot show them.

---

## Output Format

**For a single reference:**
```
In-text citation: (Author, Year)
Reference list entry:
Author, A. B. (Year). Title of work. Journal, Volume(Issue), pages. https://doi.org/xx

Missing or uncertain: [list each one, or "None"]
```

**For a reference list:**
- Corrected list in alphabetical order.
- A short list of each change made and why.
- A count: total entries, entries with missing fields, entries with changes.

---

## Common Errors to Watch For

- `doi:` prefix or a DOI that is not a link.
- `Anonymous` used as an author.
- `&` missing before the last author, or `and` used inside brackets.
- `et al.` in the reference list.
- `62 (3)` instead of `62(3)`.
- Missing a, b, c for the same author and year.
- `(Ed.)` used for two editors. Use `(Eds.)`.
- Missing issue, pages, or DOI, left blank instead of marked in red.
- Title case used for article titles.

---

## Important Reminders

- **Never fabricate.** Do not invent any part of a reference: authors, title, year, DOI, pages, publisher, or degree type. If information is missing, mark it in red.
- **Do not guess the institution or degree from a URL without saying so.** Mark the guess as `[CHECK]`.
- **Explain your corrections** briefly, so the author learns the rule, not only the fixed version.
- **If the IPS guideline and this skill disagree**, follow the IPS guideline and say so.

---

## Limits

- The EndNote style file (`.ens`) is binary. It was not fully decoded. For an exact check of a rule not listed here, tell the author to check it in EndNote's Output Styles Editor.
- This skill formats citations. It does not check that a source exists. Tell the author to verify each DOI and URL before submission.

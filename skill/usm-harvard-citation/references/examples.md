# Examples: USM Harvard (Harvard-USM Ver 2020)

Examples follow the lecture slides "Referencing" (Assoc. Prof. Dr WM Zahiruddin, MPH GKT517 USM 2023/2024) and the Harvard-USM Ver 2020 style. Fictitious details are marked. Check each against the original source before use.

## In-text citations

| Situation | Output |
|---|---|
| 1 author, outside sentence | (Smith, 2013) |
| 1 author, inside sentence | Smith (2013) described that... |
| 2 authors, outside sentence | (Zahiruddin & Naing, 2002) |
| 2 authors, inside sentence | Zahiruddin and Naing (2002) described that... |
| 3+ authors | (Wilson et al., 1997) or Wilson et al. (1997) |
| Same author, same year | (Johnson, 1994a); (Johnson, 1994b) |
| Several sources | (Smith, 1999; Jones et al., 2001; Turner & William, 2006) |
| Organisation as author | (WHO, 2013) |
| No author, title used | ("New Child Vaccine," 2001) |
| Secondary source | (Miller, 1953, as cited in Agrios, 2005) |
| Personal communication | (J. D. Black, personal communication, May 30, 2013) |

## Reference list entries

**Journal article (slide example)**
Anita, S., Zahiruddin, W. M., Sa'iah, A., Rahimah, M. A. & Sha'ari, B. N. (2007). HIV/AIDS knowledge, attitudes and risk behaviours among Orang Asli in Peninsular Malaysia. Med J Malaysia, 62(3), 227-233.

**Journal article with DOI (slide example)**
Ismail, T. A., Sulaiman, Z., Jalil, R., Muda, W. M. & Man, N. N. (2012). Breast milk expression among formally employed women in urban and rural Malaysia: A qualitative study. Int Breastfeed J, 7(1), 11. https://doi.org/10.1186/1746-4358-7-11

**Book (slide example)**
Fletcher, R., Fletcher, S. & Wagner, E. (1998). Clinical epidemiology, the essentials (2nd ed.). Baltimore, USA: Williams and Wilkins.

**Book chapter (slide example)**
Norsa'adah, B. & Nik Rosmawati, N. H. (2011). Non-parametric tests. In: Nik Rosmawati, N. H., Mohd Ismail, I. & Rohana, A. J. (Eds.), Statistics Made Easy. Basic Statistical Steps in Medical & Health Research. Kota Bharu: Department of Community Medicine, pp. 95-116.

**Webpage (slide example)**
Loney, P. L., Chambers, L. W., Bennett, K. J., Roberts, J. G. & Stratford, P. W. (2004). Critical Appraisal of the Health Research Literature Prevalence or Incidence of a Health Problem. Retrieved from http://www.phac-aspc.gc.ca/ [Accessed 17 March 2009].

**Thesis (fictitious)**
Ahmad, S. (2019). Factors influencing vaccination uptake among caregivers in Kelantan (Dissertation). Universiti Sains Malaysia, Kubang Kerian.

**Thesis found online (from user's test case)**
Adenan, A. F. (2018). The relationship between fatigue factors, job factors and environmental factors towards commuting accidents among nurses in hospital (<span style="color:red">**[MISSING: degree type]**</span>). Universiti Utara Malaysia. Retrieved from https://etd.uum.edu.my/id/eprint/8257 [Accessed 17 February 2024].

**Journal article with missing pages (from user's test case)**
Abdullah, N. D. S., Mahadi, M. R. & Baharudin, M. R. (2023). Development of mobile application in assessing commuting accident risk (CommuRisk) amongst commuters at Klang Valley. Malaysian Journal of Medicine & Health Sciences, 19(3), <span style="color:red">**[MISSING: pages]**</span>. https://doi.org/10.47836/mjmhs.19.3.14

**Organisation as author (fictitious)**
World Health Organization. (2013). Global status report on noncommunicable diseases. Geneva: WHO.

**21+ authors (format rule)**
Surname, A., Surname, B., ... (list authors 1 to 19), ..., Last Author, Z. (Year). Title...

## Common mistakes to flag

- Writing "Anonymous" instead of the organisation or title.
- Using `and` in brackets: write `&` in brackets, `and` in the sentence.
- Writing `et al.` in the reference list: list all authors up to 20.
- Missing a, b, c for same author, same year.
- Using `(Ed.)` for two editors: use `(Eds.)`.
- Not italicising journal names in Word.

## Test results (manual check, not run inside Claude)

Five references checked by reading them against SKILL.md and usm-formatting-rules.md. The skill itself was not run in the Claude app.

| # | Source | In text | Result |
|---|---|---|---|
| 1 | Ab Hamid et al., 2018 (9 authors) | (Ab Hamid et al., 2018) | Missing issue and DOI/URL (red). Page `90` may be an article number (check). |
| 2 | Abdullah et al., 2023 | (Abdullah et al., 2023) | Missing pages (red). DOI in `https://doi.org/` form. |
| 3 | Adams et al., 2023 (7 authors) | (Adams et al., 2023) | Pages missing (red). `61` is an article number, not a page range. Corrected after the headless Claude Code test. |
| 4 | Adenan, 2018 (online thesis) | (Adenan, 2018) | Missing degree type (red). Institution inferred from URL (check, red). |
| 5 | Ali et al., 2016 (4 authors) | (Ali et al., 2016) | Missing DOI/URL (red). Title `Roads traffic accidents` may need correction (check, red). |

Alphabetical order: Ab Hamid, Abdullah, Adams, Adenan, Ali. Correct.

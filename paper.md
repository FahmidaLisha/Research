# How Much Did COVID-19 Raise Unemployment Across Indian Regions? An Exploratory Analysis of Monthly Data, May 2019 to June 2020

## Abstract

This study asks how unemployment in India changed around the COVID-19 lockdown and how the change differed across regions and between rural and urban areas. It uses a monthly dataset of 740 region-level records covering 28 Indian regions from May 2019 to June 2020. The method is exploratory data analysis in Python: regional averages, monthly trends, an urban-rural split, and a comparison of the periods before and after March 2020. The key result is a sharp but temporary rise. The average unemployment rate across records was 9.5% before March 2020 and 17.8% afterwards. Monthly averages reached 23.6% in April and 24.9% in May 2020, then fell to 11.9% in June. Labour participation fell from 43.9% to 39.3% over the same split. Urban areas were hit harder than rural ones, and regional differences were large. The findings are descriptive: they use unweighted averages over a short window and do not show causation.

## 1. Introduction

India introduced a nationwide lockdown on 24 March 2020 to contain COVID-19. It was extended several times and expired on 31 May, after which restrictions were relaxed in phases [3]. Because it halted most economic activity at once, the lockdown is a rare natural experiment for labour-market research, and the question of this paper follows directly: **how large was the rise in unemployment, how long did it last, and where was it concentrated?**

The literature reviewed for this paper points to four themes. First, the shock was immediate. Vyas, using CMIE's household panel, reports that unemployment jumped as soon as the lockdown began, and that the labour participation rate dropped sharply between March and April 2020 [1]. Bertrand and co-authors put the April unemployment rate at nearly 25% and describe a quick rebound once restrictions eased [3]. Second, the unemployment rate alone can mislead. The same authors note that people who stop looking for work leave the labour force and so disappear from the rate, and they find that the share of the population in work stayed below its pre-lockdown level for months [3]. This is why labour participation is examined here as well. Third, the burden was uneven across groups: Deshpande finds that the lockdown's early effects on job loss differed by gender [2], and the State of Working India 2021 report documents lasting income losses and a shift toward informal work [4]. Fourth, regions differed. Bertrand et al. show large state-level variation in how deep the downturn was and how fast recovery came [3].

Against this background, the present paper uses a publicly shared monthly dataset to measure the size and timing of the shock, to compare regions, and to compare rural and urban areas. It does not try to explain the causes, which the cited studies address with richer household data.

## 2. Methodology

**Data.** The analysis uses `Unemployment_in_India.csv`, which holds monthly estimates for 28 regions from 31 May 2019 to 30 June 2020, split by rural and urban area. The variables are the estimated unemployment rate, the estimated number employed, and the estimated labour participation rate. The file does not state its source; its variables resemble those of CMIE's household survey, but this could not be confirmed.

**Cleaning.** Column names were trimmed, and 28 rows in which every field was empty were removed, leaving 740 records. Dates were parsed day-first and sorted.

**Analysis.** Following the Assignment 2 notebook, the analysis (i) averaged the unemployment rate by region and by month, (ii) computed correlations among unemployment, employment and participation, and (iii) split the records at 1 March 2020 into a pre-COVID group (536 records) and a post-COVID group (204 records). Three additions were made for this paper: a rural-urban comparison, a regional measure of change, and a sensitivity check that drops March 2020 from the post group. All averages are simple (unweighted) means of the reported rates. The work used Python with pandas, Matplotlib and Seaborn; `analysis.py` regenerates every figure and table. The full description is in `methodology.md`.

## 3. Results

### 3.1 Before and after

**Table 1. Average unemployment and labour participation before and after 1 March 2020**

| Period | Avg unemployment rate (%) | Avg labour participation (%) | Records |
|---|---|---|---|
| Pre-COVID (May 2019 – Feb 2020) | 9.51 | 43.89 | 536 |
| Post-COVID (Mar – Jun 2020) | 17.77 | 39.33 | 204 |

The average unemployment rate rose by 8.3 percentage points, an increase of about 87% in relative terms, while labour participation fell by 4.6 points (Table 1, Figure 4).

![Figure 4](figures/fig4_pre_post.png)

### 3.2 Month-by-month path

Figure 1 shows that unemployment was stable between about 8.9% and 10.0% from May 2019 to February 2020 and edged up to 10.7% in March 2020. It then jumped to 23.6% in April and 24.9% in May, and fell back to 11.9% in June. Labour participation followed the opposite path, dropping from 43.1% in March to 35.1% in April before recovering partly to 40.6% in June. Because March contains only a few days of lockdown, it pulls the post-COVID average down: for April to June alone the average unemployment rate is 20.2%, and for April to May it is 24.3%.

![Figure 1](figures/fig1_monthly_trend.png)

### 3.3 Regional differences

Average unemployment over the whole period differed widely across regions (Table 2, Figure 2). Tripura (28.4%) and Haryana (26.3%) had the highest averages, followed by Jharkhand (20.6%) and Bihar (18.9%). At the other end, Meghalaya averaged 4.8%. Measured as the change from a region's own pre-COVID average to its April-May 2020 average, the largest rises were in Puducherry (+73.8 points), Jharkhand (+42.8), Tamil Nadu (+38.0) and Bihar (+33.4). Each region contributes between 12 and 28 records, so individual regional figures should be read with caution.

**Table 2. Ten regions with the highest average unemployment rate, May 2019 – June 2020**

| Region | Avg unemployment rate (%) |
|---|---|
| Tripura | 28.35 |
| Haryana | 26.28 |
| Jharkhand | 20.58 |
| Bihar | 18.92 |
| Himachal Pradesh | 18.54 |
| Delhi | 16.50 |
| Jammu & Kashmir | 16.19 |
| Chandigarh | 15.99 |
| Rajasthan | 14.06 |
| Uttar Pradesh | 12.55 |

![Figure 2](figures/fig2_top10_regions.png)

### 3.4 Urban and rural areas

Urban areas had higher unemployment throughout (Figure 3). The pre-COVID average was 10.8% in urban and 8.1% in rural areas; the post-COVID average was 19.3% and 16.2%. The gap was widest in May 2020, at 28.4% urban against 21.2% rural. By June 2020 the two were nearly equal (12.0% and 11.8%).

![Figure 3](figures/fig3_urban_rural.png)

### 3.5 Correlations

Across all records, unemployment correlates weakly and negatively with the number employed (r = −0.22) and not at all with labour participation (r = 0.00). Employment counts largely reflect the size of a region, so these coefficients say little about the lockdown's effect.

## 4. Discussion

The central finding is a sharp, short-lived spike. Unemployment was about 2.4 to 2.5 times its February level in April and May, then returned close to its earlier range by June. This agrees in shape with the household-survey literature, which reports a near-immediate jump and a fast rebound once restrictions eased [1], [3]. The average here for April (23.6%) is of similar size to the national figure of nearly 25% reported by Bertrand et al., although the two are not directly comparable because the figure in this paper is an unweighted average across regions [3].

The fall in labour participation matters as much as the rise in unemployment. Participation dropped by about 8 points between March and April and was still below its earlier level in June. This supports the caution in the literature that a falling unemployment rate can partly reflect people leaving the labour force, not people finding work [3]. The June rate of 11.9% therefore should not be read as full recovery; it is above the 9.5% pre-COVID average, and participation had not returned to 43–44%.

The urban-rural gap, with urban areas more affected in April and May, fits the picture of a shock concentrated in activities that stopped under the lockdown, but this dataset cannot identify the sectors involved. The large differences between regions, such as the extreme rises in Puducherry and Jharkhand, are consistent with the state-level variation reported elsewhere [3]; explaining them would require data on industry mix, lockdown enforcement, and migration, which this dataset lacks. The literature also shows that outcomes differed by gender and by formality of work [2], [4], neither of which can be examined here.

**Limitations.**
1. *Short window.* Only ten pre-COVID months are available, so seasonal patterns and earlier trends cannot be separated from the lockdown effect.
2. *Unweighted averages.* Regions and area types are averaged equally regardless of population, so the figures are not national rates.
3. *Period definition.* The split at 1 March 2020 puts a nearly lockdown-free month in the post group. The April-June and April-May averages above show how sensitive the result is to this choice.
4. *Unknown provenance.* The dataset's source and method are not documented in the file, and survey definitions of employment differ across sources [1].
5. *No weighting, tests or causal design.* Results are descriptive; no confidence intervals or significance tests are reported, and correlation is not causation.
6. *Uneven coverage.* Some regions have as few as 12 records, and records per month vary from 50 to 55.

## 5. Conclusion

Using 740 monthly region-level records from May 2019 to June 2020, this paper finds that the average unemployment rate rose from 9.5% before March 2020 to 17.8% afterwards, peaking at 24.9% in May 2020 before falling to 11.9% in June, while labour participation fell from 43.9% to 39.3%. The rise was larger in urban areas and very uneven across regions. The pattern matches the sharp-shock, fast-rebound shape described in the household-survey literature, but the short window, unweighted averages and undocumented source mean the results are indicative rather than definitive. Future work should use population-weighted data, a longer pre-lockdown baseline, and sector and gender breakdowns.

## References

[1] M. Vyas, "Impact of Lockdown on Labour in India," *The Indian Journal of Labour Economics*, vol. 63, 2020. doi: 10.1007/s41027-020-00259-w.

[2] A. Deshpande, "Early Effects of Lockdown in India: Gender Gaps in Job Losses and Domestic Work," *The Indian Journal of Labour Economics*, vol. 63, suppl. 1, pp. 87–90, 2020.

[3] M. Bertrand, R. Dizon-Ross, K. Krishnan, and H. Schofield, "Employment, Income, and Consumption in India During and After the Lockdown: A V-Shape Recovery?," Rustandy Center for Social Sector Innovation, Univ. of Chicago Booth School of Business, Nov. 2020. [Online]. Available: https://www.chicagobooth.edu/research/rustandy/stories/employment-income-and-consumption-in-india-during-and-after-the-lockdown

[4] Centre for Sustainable Employment, Azim Premji University, *State of Working India 2021: One Year of Covid-19*. Bengaluru, India, Apr. 2021.

# Unemployment in India around the COVID-19 lockdown

An exploratory analysis of monthly unemployment data for 28 Indian regions (May 2019 – June 2020), written up as a short research paper.

## Start here
| Item | File |
|---|---|
| Paper | [paper.md](paper.md) |
| Methodology | [methodology.md](methodology.md) |
| Notebook (Assignment 2) | [notebook.ipynb](notebook.ipynb) |
| Slides (7 slides) | [slides.pptx](slides.pptx) |
| References (Zotero-importable) | [references.bib](references.bib) |

## Key result
The average unemployment rate across records rose from 9.5% before March 2020 to 17.8% afterwards, peaking at 24.9% in May 2020 and falling to 11.9% in June. Labour participation fell from 43.9% to 39.3%.

## Reproduce the figures and tables
```bash
pip install pandas matplotlib seaborn
python analysis.py
```
Figures are written to `figures/` and tables to `tables/`.

## Repository layout
```
paper.md            methodology.md      references.bib
notebook.ipynb      analysis.py         slides.pptx (built by build_deck.js)
data/Unemployment_in_India.csv
figures/            tables/
```

## Data note
The CSV does not state its original source. Its variables resemble CMIE's household-survey indicators, but this has not been verified. Averages in the paper are unweighted and descriptive.

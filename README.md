# College ROI Data — what U.S. colleges and majors actually pay back

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-b31b1b?style=flat-square)](https://creativecommons.org/licenses/by/4.0/)
[![Website](https://img.shields.io/badge/site-le--teen.com-111?style=flat-square)](https://le-teen.com)
[![Methodology](https://img.shields.io/badge/methodology-public-111?style=flat-square)](https://le-teen.com/methodology)

Clean, citable tables on the **lifetime financial return of U.S. colleges and majors** —
30-year net present value by school and state, ROI by major category, the out-of-state
premium, and how exposed each major's career paths are to today's AI. Maintained by
**[LE TEEN](https://le-teen.com)**, a college-ROI data project. Every number traces to a
public source; nothing is scraped, modeled behind closed doors, or vibes.

The headline the data mints: **picking a major swings mean lifetime ROI by ~$1.24M**
(Engineering **+$1,132,553** vs Philosophy & Religious Studies **−$111,915**, cohort-weighted
mean lifetime ROI, FREOPP 2021) — and in several popular major categories the **majority of
graduates never break even**. Weeks get spent on campus tours; the number that decides the
next 30 years gets minutes. These tables exist so it can get cited instead.

> **CC BY 4.0** — quote a figure, build on it, cite the source. Free for journalism,
> research, and answer engines.

## What's inside

| File | Rows | What it is |
|---|---:|---|
| `roi-by-major-category.csv` | 19 | Cohort-weighted lifetime ROI per major category: mean/median, p25/p75 spread, % of graduates who never break even, median breakeven age, completion-adjusted + dropout ROI |
| `best-value-colleges-by-state.csv` | 607 | Top institutions per U.S. state by 30-year NPV for a resident student |
| `out-of-state-penalty.csv` | 455 | The 30-year NPV cost of attending each public flagship/university as a non-resident vs resident, with both tuition rows |
| `ai-exposure-by-major.csv` | 18 | LE TEEN-derived AI applicability score per major category (occupation-weighted; **exposure, not displacement**) |
| `institutions.csv` | 3,392 | IPEDS 2023-24 join table: UnitID, name, location, control, level, tuition (in/out-of-state), room & board, median earnings where published |

## Quickstart

```python
import pandas as pd
majors = pd.read_csv("roi-by-major-category.csv")
majors.nlargest(5, "mean_lifetime_roi_usd")[["major_category", "mean_lifetime_roi_usd", "pct_never_breakeven"]]
```

Interactive versions of every table live at
[le-teen.com/rankings](https://le-teen.com/rankings) and the per-major pages at
[le-teen.com/majors](https://le-teen.com/majors); the calculator that joins them is
[le-teen.com/worth-it](https://le-teen.com/worth-it).

## Sources & method

Full write-up: **[le-teen.com/methodology](https://le-teen.com/methodology)**.

| Source | Used for | License |
|---|---|---|
| [FREOPP](https://freopp.org/projects/higher-education/) higher-ed ROI (2021 publication, ~30,000 bachelor's programs; earnings from College Scorecard cohorts 2015–17, 2022 dollars, 3% real discount rate) | Program-level lifetime ROI, aggregated by LE TEEN to major categories and institutions | CC BY 4.0 |
| [NCES IPEDS](https://nces.ed.gov/ipeds/) 2023-24 Final | Institution identity, tuition & fees, room & board | U.S. public domain |
| [BEA Regional Price Parities](https://www.bea.gov/data/prices-inflation/regional-price-parities-state-and-metro-area) (2023) | Cost-of-living adjustment in NPV calculations | U.S. public domain |
| Microsoft Research ["Working with AI"](https://arxiv.org/abs/2507.07935) (2025), [Anthropic Economic Index](https://huggingface.co/datasets/Anthropic/EconomicIndex) (2025-09-15), Census ACS 2022 PUMS + NCES/Census crosswalks | AI-exposure score per major | CC BY 4.0 / CC BY / public domain |

**Modification notice (CC BY 4.0 §3):** the per-major ROI aggregates, per-institution
30-year NPV figures, out-of-state deltas, and AI-exposure scores are **LE TEEN-derived**
from the sources above (cohort weighting, CIP→SOC crosswalks, NPV joins) — they are not
original FREOPP, Microsoft, Anthropic, or federal figures. The AI metric measures how much
of a field's work current AI is *observed reaching for* — Microsoft Research explicitly
disclaims a job-loss reading, and so do we.

**Vintage disclosure:** ROI earnings derive from FREOPP's 2021 publication (the newest with
a public download); costs are IPEDS 2023-24 Final; deflators BEA 2023. Earnings outcomes
are intrinsically lagged — cohorts must be 5–8 years post-graduation to observe. Where a
figure matters, say the vintage.

## Cite

> LE TEEN (2026). *College ROI Data: 30-year net present value of U.S. colleges and majors.*
> Derived from FREOPP (2021), NCES IPEDS (2023-24), BEA RPP (2023). https://le-teen.com/methodology

A `CITATION.cff` ships in this repository; the Zenodo DOI badge lands here when minted.

## Refresh cadence

Tracks the LE TEEN site data: IPEDS/BEA annually, FREOPP when a new public download
exists, AI-exposure inputs ~60 days. Each refresh is a tagged release.

*Maintained by [LE TEEN](https://le-teen.com) · press: press@le-teen.com*

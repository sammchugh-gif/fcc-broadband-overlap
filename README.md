# US cable operator footprint overlap — FCC Broadband Data Collection, December 2025

Competitive overlap for the five largest US cable operators, computed location-by-location from the
FCC's Broadband Data Collection (BDC) fixed-availability files, availability **as of 31 December 2025**
(published by the FCC on 18 August 2026).

**Unit of analysis: the Broadband Serviceable Location (BSL)** as defined by the FCC/CostQuest Fabric —
not homes passed. A multi-tenant building counts as one location, so these counts run below
operator-reported passings, most of all in dense markets.

**Covers cable (technology code 40) and fibre-to-the-premises (code 50) only.** Copper, fixed wireless
and satellite are excluded, so telco counterparties appear here on their fibre footprints alone.

Charter and Cox are held **separate, as filed**, because the vintage precedes their 20 August 2026 combination.

## Summary

| Operator | Footprint (BSLs) | Own fibre | Another fibre filer | Another cable filer | Uncontested |
|---|---:|---:|---:|---:|---:|
| Comcast (Xfinity) | 38,786,664 | 2.4% | 59.7% | 9.6% | **36.3%** |
| Charter (Spectrum) | 35,944,137 | 6.4% | 59.0% | 6.6% | **38.3%** |
| Cox | 7,297,869 | 11.7% | 56.8% | 2.9% | **42.2%** |
| Optimum (Altice USA) | 5,366,001 | 42.4% | 73.4% | 5.1% | **25.2%** |
| Cable One (Sparklight) | 2,280,032 | 10.2% | 55.2% | 13.3% | **37.5%** |

*Uncontested* = the share of an operator's own footprint at which **no other provider** reports cable or
fibre availability.

## Largest counterparties

As filed, and rolled up to current parents after the 2026 transactions:

| Operator | 1st | 2nd | 3rd | AT&T+Lumen | Verizon+Frontier |
|---|---|---|---|---:|---:|
| Comcast | AT&T 21.0% | Verizon Fios 14.1% | Lumen 5.2% | 26.2% | 18.2% |
| Charter | AT&T 22.5% | Frontier 10.7% | Google Fiber 3.3% | 23.0% | 13.5% |
| Cox | AT&T 21.4% | Verizon Fios 10.8% | Lumen 8.9% | 30.0% | 12.9% |
| Optimum | Verizon Fios 34.3% | AT&T 10.2% | Frontier 7.7% | 10.3% | 42.0% |
| Cable One | AT&T 12.2% | Comcast 5.0% | Frontier 4.6% | 15.9% | 4.6% |

Two observations that fall out of the cross-operator comparison:

- **AT&T is the counterparty for almost the whole industry.** It is the largest overlapping operator for
  four of the five (Optimum's is Verizon). Between **90.2% and 96.1%** of AT&T's 19.4 million-BSL fibre
  footprint sits inside one of these five cable footprints — the sum of the pairwise intersections is
  96.1%, and the maximum possible cable-on-cable double count is 1.14 million BSLs.
- **After the 2026 deals, two telco balance sheets cover 36–52% of every large cable footprint.** Before
  them, that exposure was spread across four or five independent counterparties.

## Files

| File | Contents |
|---|---|
| `Cable_operators_overlap_FCC_BDC_Dec2025.xlsx` | Full workbook: summary, one ranked sheet per operator, by state, state × operator detail, method |
| `data/summary.csv` | The summary table above |
| `data/<operator>_overlap_by_operator.csv` | Every operator overlapping that cable operator, ranked |
| `data/by_state.csv` | Footprint and exposure by state, all five |
| `data/state_x_operator.csv` | 2,678 state × operator pairs |

CSVs render as sortable tables in the GitHub web UI; the `.xlsx` downloads.

## Definitions

- **Footprint** — unique BSLs at which the operator reports cable or FTTP availability with
  `business_residential_code` R or X (residential or mixed). No speed floor.
- **Overlap(A, X)** — the number of A's BSLs at which operator X also reports qualifying availability.
  `pct_of_target_footprint` divides by A; `pct_of_their_footprint` divides by X. The matrix is **not**
  symmetric.
- **Operator roll-ups** — by brand name and the FCC provider list. Current parents reflect: AT&T's
  acquisition of Lumen's Mass Markets fibre (closed 2 Feb 2026), Verizon's acquisition of Frontier
  (20 Jan 2026), Charter–Cox (20 Aug 2026), and the Metronet/Lumos T-Mobile joint ventures.

## Caveats

1. Availability is **provider-reported** under the BDC "served" standard, which includes locations the
   filer states it could serve within ten business days at standard installation charges. Overlap derived
   this way runs above company-disclosed overlap.
2. BSLs are not homes passed (see above).
3. Brand-based roll-ups can misclassify small filers whose brand resembles a large operator's. Large
   operators' brand names in BDC data are unambiguous.
4. Copper is not included.

## Verification

48 values — footprints, any-other-fibre, any-other-cable and every pairwise count — reproduce an earlier
independent run of the same source data through a different code path. Cable One sits at rank 11 nationally
and so falls outside that comparison matrix; only its footprint could be cross-checked, and it matched.

## Source

FCC National Broadband Map, Broadband Data Collection fixed availability, as of 31 December 2025:
https://broadbandmap.fcc.gov/data-download/nationwide-data

The underlying FCC data is a US Government work. This analysis is provided as-is, with no warranty.

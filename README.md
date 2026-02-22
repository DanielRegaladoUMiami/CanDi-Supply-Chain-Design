# CanDi Supply Chain Network Design

> **Supply Chain Analytics — Final Project**
> University of Miami, Herbert Business School

## Overview

CanDi (CandyDistributor) is a private equity-backed company that distributes European soft candies across the New England states. After 2 years relying on expensive 3PL distributors, CanDi needs to design its own supply chain infrastructure — deciding where to place distribution centers, how to transport product, and how to manage inventory.

This project delivers a complete supply chain design including structural decisions and detailed operational parameters.

## Key Findings

| Metric | Value |
|--------|-------|
| Annual Revenue | $22.2M |
| Weekly Volume | 329K bags / 274 pallets |
| SKUs | 110 across 5 segments |
| States Served | CT, MA, ME |

### Recommendation: Open CT + MA Distribution Centers

- **Total annual cost: $1.67M** — saving ~$1M/year vs. direct delivery from New York
- FTL trunk-line from NY to DCs: **$0.02/bag** vs. $0.15/bag LTL direct
- 3PL at leased DCs handles last-mile delivery and customer scheduling
- Maine excluded — $200K fixed cost not justified for only 4% of total volume
- Mixed pallet surcharge of $117K/year accepted (FTL savings far outweigh it)

### Inventory Policy

- **Periodic Review (R,S)** — weekly review cycle aligned to customer ordering
- R = 1 week, L = 1 day, z = 1.645 (95% service level)
- Order-up-to level: S = μ×(R+L) + z×σ×√(R+L)
- Total safety stock: **37 pallets** across both DCs ($27K/year holding cost)
- Inventory turns: 60–93× per year
- All 110 SKUs stocked at both DCs for full availability

## Repository Contents

| File | Description |
|------|-------------|
| `CanDi_Supply_Chain_Analysis.ipynb` | Full Jupyter notebook with data analysis, demand aggregation, transportation cost modeling, warehouse configuration evaluation, surcharge analysis, and inventory policy design |
| `CanDi_Supply_Chain_Presentation.pptx` | 8-slide executive presentation for CanDi management team |
| `CanDi_Supply_Chain_Presentation.pdf` | PDF export of the presentation |

## Methodology

1. **Demand Aggregation** — Computed weekly demand per state by segment, converted to pallets
2. **Transportation Analysis** — Compared FTL, LTL, leased truck, and UPS/FedEx across all routes
3. **Warehouse Enumeration** — Evaluated all 2³ = 8 combinations of CT, MA, ME distribution centers
4. **Cost Breakdown** — Decomposed total cost into transportation, fixed DC costs, surcharges, and inventory
5. **Surcharge Analysis** — Modeled the $1/box mixed-pallet fee by product segment and region
6. **Inventory Design** — Applied Periodic Review (R,S) policy with demand pooling at DCs

## Key Assumptions

- Normally distributed demand (per case instructions)
- All customers in a region behave identically for any given SKU
- 20 pallets max per truck, no stacking
- $200K/year fixed cost per leased DC
- 25% annual holding cost rate on $0.80/bag product cost
- 95% service level (z = 1.645)

## Tools & Libraries

- **Python**: pandas, numpy, matplotlib, seaborn, scipy
- **Presentation**: PptxGenJS (Node.js)

---

*Daniel Regalado Cardoso — University of Miami*

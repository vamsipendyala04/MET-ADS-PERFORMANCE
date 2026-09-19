# Meta Ads Performance Optimization: Cleaning, EDA & Decision Framework

Cleaned a raw Meta Ads export (semi-structured JSON, 644 columns) and analyzed it to decide which ads, ad sets and campaigns to **scale, pause or discontinue**.

**Tools:** Excel (cleaning, pivots) · Python · Pandas · NumPy · Matplotlib · Seaborn

## Snapshot

| | |
|---|---|
| Dataset | 237 ads, 72 columns (reduced from 644) |
| Levels | Campaign, ad set and ad |
| Platforms | Facebook, Instagram, Threads |
| Outcome | 24 ads to keep, 183 paused, 30 to discontinue |
| Top platform | Threads |
| Best day | Tuesday |

## Workflow

**1. Excel: cleaning and structuring**
- Flattened embedded JSON targeting (age range, interests, behaviors, geo-location) into columns and dropped the raw JSON.
- Standardized dates, currency and numeric fields; enforced unique Ad IDs; cleaned text-based NaNs.
- Cut 644 columns to 72 by dropping fields that were 80-90% null, hourly and weekday breakdowns (recomputable from date) and derivable metrics such as Ad Rank.
- Engineered Engagement Rate and Conversion Rate (24-hour, 7-day, overall), monthly performance and date-based columns.

**2. Excel: pivot analysis**
- Platform level: spend, conversions, average CPC, conversion rate.
- Campaign level: payments, cost per landing page view (CPLPV), ROI %, CTR %.
- Daily level: payments, CPC and conversion trends.

**3. Python: EDA**
- KPI recalculation to validate the Excel figures, null and anomaly checks, distributions, outlier detection and correlations.
- Platform comparison, campaign efficiency benchmarking, and payments by gender, age range and start date.

## Key Findings

### Ad-level decisions (237 ads)

| Decision | Ads | Criteria |
|---|---|---|
| Continue | 24 | High CTR, low CPC, strong conversion rate |
| Pause | 183 | Near-average CTR, moderate CPC, inconsistent conversions |
| Discontinue | 30 | Low CTR, high CPC, poor conversion, zero payments despite spend |

Ads to continue by platform: **Threads 11**, Instagram 7, Facebook 6. Threads is the strongest platform.

### Timing
**Tuesday** performs best: 308 payments, the lowest CPC (₹3.5) and an above-average conversion rate. Shift more budget to Tuesdays.

### Campaigns

| Campaign | Verdict | Evidence |
|---|---|---|
| VM \|\| Delhi NCR \|\| Traffic | Scale | Lowest CPC ₹1.16, 568 payments (most), 0.77% conversion rate |
| Web App \| Conversion | Optimize | Highest spend (₹181K+), high CPC ₹13.26, low conversion 0.37% |
| VM Brand Awareness | Keep for reach only | 8.79% of spend; good for reach, weak on payments |
| ToF Engagement, Straight Outta | Discontinue | 0 payments, budget consumed |

### Ad sets

| Ad set | Verdict | Evidence |
|---|---|---|
| Women - Clubbed Audience | Scale | 567 payments, lowest CPLPV ₹2.30, 0.81% conversion |
| RMK - Waitlist | Maintain | 1.05% conversion, CPLPV ₹18.50 |
| Dating Apps, Entrepreneurship Insta, Travel Insta, Interest-Based Dinner | Discontinue | 0 payments, budget leakage |

### Ads
- **Top 5 by spend share and payments:** Monkey UGC, Ad 1 (5 Strangers), Saturday Night, Ranveer, Instagram Post (Latest StepOut Dinner).
- **Most efficient 3 (scale):** Monkey UGC, Saturday Night, Ranveer, each with CPLPV under ₹1.5 and about 0.70% conversion.

## Metric Definitions

| Metric | Formula |
|---|---|
| CTR (%) | Clicks ÷ Impressions × 100 |
| CPC | Spend ÷ Clicks |
| Conversion Rate | Conversions ÷ Clicks |
| CPA | Spend ÷ Conversions |
| CPLPV | Spend ÷ Landing Page Views |
| Engagement Rate | Engagements ÷ Impressions |
| ROI (%) | (Revenue − Spend) ÷ Spend × 100 |
| Metric Ratio | Ad metric ÷ group average (< 0.85 underperforming, > 1.15 overperforming) |

All KPIs were calculated in Excel and re-validated in Pandas.


```

## Skills Demonstrated

Handling semi-structured marketing data · KPI modeling and benchmarking · Campaign optimization · Data-driven scale/pause/stop decisions

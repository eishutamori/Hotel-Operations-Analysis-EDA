# Hotel Booking Demand — Exploratory Data Analysis (EDA02)

An end-to-end Exploratory Data Analysis (EDA) of **Elite Hotels International's** reservation dataset (`hotel_bookings.csv`), evaluating booking behavior, cancellation drivers, pricing dynamics (ADR), seasonality, and market segmentation across **City Hotel** and **Resort Hotel** properties.

---

## Project Overview

* **Dataset:** `hotel_bookings.csv` (`119,390` raw rows → `87,396` deduplicated bookings across **2015–2017**, `32` original features + engineered features)
* **Scope:** **25 structured business questions** organized into three progressive tiers:
  * **Basic Level (10 Questions):** Lead time distribution, hotel type share, overall cancellation rate, peak booking months, special requests, guest country origin (`PRT` 31.41%, `GBR` 11.94%, `FRA` 10.11%), ADR summary, parking demand, stay duration, and booking channels.
  * **Medium Level (10 Questions):** Cancellation rate by hotel type, ADR by market segment, lead time vs. cancellation correlation, top distribution channel, previous cancellations by hotel, multi-year ADR trend, highest-revenue month, special requests vs. ADR, stay duration for repeated vs. new guests, and most booked room types.
  * **Advanced Level (5 Questions):** Logistic regression on cancellation predictors, multiple linear regression of ADR on guest composition (`adults`, `children`, `babies`), correlation between booking changes and special requests, seasonal cancellation patterns, and lead time box-plot distributions across market segments.

---

## Key Findings

| Metric / Dimension | Key Result |
|---|---|
| **Property Mix** | **City Hotel:** `53,428` bookings (`61.13%`) \| **Resort Hotel:** `33,968` bookings (`38.87%`) |
| **Overall Cancellation Rate** | **27.49%** (`24,025` canceled) — **City Hotel (30.04%)** vs. **Resort Hotel (23.48%)** |
| **Peak Demand & Revenue** | **August** leads in bookings (`11,257`), ADR (`150.88`), and total ADR sum (`1,698,412.48`) |
| **Multi-Year ADR Growth** | Rose **+28.81%** from **2015 (`92.16`)** → **2016 (`101.54`)** → **2017 (`118.71`)** |
| **Top Distribution Channel** | **TA/TO** (`69,141` bookings, `79.11%`), followed by **Direct** (`12,988`, `14.86%`) |
| **Top Room Category** | **Room Type A** (`56,552` bookings, `64.71%`), followed by **Type D** (`19.91%`) |
| **Cancellation Predictors (Logit)** | **Previous cancellations (`OR = 2.59`)** & **lead time (`OR = 1.005/day`)** increase risk; **repeated guest (`OR = 0.19`)**, **booking changes (`OR = 0.61`)**, and **special requests (`OR = 0.63`)** reduce risk |
| **Guest Composition & ADR (OLS)** | **Children (`+38.66`)**, **Adults (`+21.18`)**, and **Babies (`+6.71`)** significantly raise ADR (`R² = 0.1649`) |

---

## Repository Structure

```text
EDA02/
├── hotel_bookings.csv          # Source dataset
├── hotel_booking_eda.ipynb     # Complete Jupyter Notebook with code, charts, and conclusions
└── README.md                   # Project documentation and key findings
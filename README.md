# Hotel Booking Demand — Exploratory Data Analysis (EDA02)

A comprehensive Exploratory Data Analysis (EDA) case study for **Elite Hotels International** (`hotel_bookings.csv`), structured into a complete **Case Study Document**, **Solution Guide** (25 Basic, Medium, and Advanced questions), and **Additional Resources**.

---

## 1. Case Study Overview & Problem Statement

**Elite Hotels International** seeks to reduce revenue leakage from reservation cancellations (**27.49%** overall) and optimize room pricing across its **City Hotel** and **Resort Hotel** properties. Using historical reservation records from **2015 to 2017**, this project investigates:
* What behavioral, seasonal, and booking-channel factors drive cancellations.
* How Average Daily Rate (ADR) responds to guest composition, market segments, special requests, and multi-year demand trends.
* How operational teams can tailor deposit policies, dynamic pricing, and loyalty programs using data-backed evidence.

---

## 2. Data Dictionary

* **Dataset:** `hotel_bookings.csv` (`119,390` raw records → `87,396` deduplicated bookings across `32` attributes)

| Feature | Type | Description |
|---|---|---|
| `hotel` | Categorical | Hotel type (`City Hotel` or `Resort Hotel`) |
| `is_canceled` | Binary | `1` if the booking was canceled, `0` if checked out |
| `lead_time` | Numeric | Days elapsed between booking date and arrival date |
| `arrival_date_year` | Numeric | Year of arrival (`2015`–`2017`) |
| `arrival_date_month` | Categorical | Month of arrival (`January`–`December`) |
| `stays_in_weekend_nights` | Numeric | Weekend nights (Sat/Sun) booked |
| `stays_in_week_nights` | Numeric | Weekday nights (Mon–Fri) booked |
| `adults` / `children` / `babies` | Numeric | Guest headcount breakdown per booking |
| `meal` | Categorical | Meal plan (`BB`, `HB`, `FB`, `SC`, `Undefined`) |
| `country` | Categorical | Guest country code (ISO 3166-1 alpha-3) |
| `market_segment` | Categorical | Segment (`Online TA`, `Offline TA/TO`, `Groups`, `Direct`, `Corporate`, `Complementary`, `Aviation`) |
| `distribution_channel` | Categorical | Acquisition channel (`TA/TO`, `Direct`, `Corporate`, `GDS`) |
| `is_repeated_guest` | Binary | `1` if returning guest, `0` if new guest |
| `previous_cancellations` | Numeric | Prior canceled bookings by the guest |
| `reserved_room_type` | Categorical | Anonymized reserved room category (`A`–`P`) |
| `booking_changes` | Numeric | Number of amendments made prior to arrival |
| `deposit_type` | Categorical | Deposit policy (`No Deposit`, `Non Refund`, `Refundable`) |
| `customer_type` | Categorical | Customer contract category (`Transient`, `Transient-Party`, `Contract`, `Group`) |
| `adr` | Numeric | Average Daily Rate (lodging revenue per night) |
| `required_car_parking_spaces` | Numeric | Parking spaces requested by the guest |
| `total_of_special_requests` | Numeric | Count of special requests (e.g., high floor, extra bed) |

---

## 3. Solution Guide Summary (25 Questions)

### Basic-Level Insights (10 Questions)
* **Property Distribution:** **City Hotel** accounts for `53,428` bookings (`61.13%`) vs. **Resort Hotel** at `33,968` (`38.87%`).
* **Baseline Cancellation Rate:** **27.49%** (`24,025` canceled bookings out of `87,396`).
* **Peak Arrival Months:** **August** (`11,257` bookings) and **July** (`10,057` bookings).
* **Top Guest Origins:** **Portugal (`PRT`, 31.41%)**, **United Kingdom (`GBR`, 11.94%)**, and **France (`FRA`, 10.11%)**.
* **ADR & Stay Benchmarks:** Mean ADR = `106.34` (Median: `98.10`); average stay = `3.63 nights` (`2.63` week nights + `1.01` weekend nights).

### Medium-Level Insights (10 Questions)
* **Cancellations by Property:** **City Hotel (`30.04%`)** cancels significantly more than **Resort Hotel (`23.48%`)** and has a higher average prior-cancellation rate (`0.0358` vs. `0.0220`).
* **Channel & Segment Economics:** **TA/TO** brings **79.11%** of volume (`69,141` bookings); **Online TA** (`115.66`) and **Transient** guests (`110.14`) command the highest ADRs.
* **Multi-Year ADR & Revenue:** Mean ADR increased **+28.81%** from **2015 (`92.16`)** to **2017 (`118.71`)**; **August** leads total ADR revenue (`1,698,412.48`).
* **Guest Loyalty & Room Popularity:** **New guests** stay nearly twice as long (`3.70` nights vs. `1.93` nights for repeated guests); **Room Type A** captures **64.71%** of bookings (`56,552`).

### Advanced-Level Insights (5 Questions)
* **Cancellation Drivers (Logistic Regression):** All predictors statistically significant (`p < 0.001`). **Previous cancellations (`OR = 2.59`)**, **ADR (`OR = 1.007`)**, and **lead time (`OR = 1.005/day`)** increase cancellation odds, whereas **repeated guest status (`OR = 0.19`)**, **booking changes (`OR = 0.61`)**, and **special requests (`OR = 0.63`)** reduce cancellation risk.
* **ADR by Guest Composition (Multiple Linear Regression, `R² = 0.1649`):** Each **child (`+38.66`)**, **adult (`+21.18`)**, and **baby (`+6.71`)** significantly raises nightly ADR (`p < 0.001`).
* **Booking Changes vs. Special Requests:** Very weak positive correlation (`r = 0.0161`), showing itinerary amendments and stay preferences behave independently.
* **Seasonal Cancellation Cycle:** Cancellations peak in **Summer (`31.55%`, August `32.18%`)** and drop to their lowest point in **Autumn (`23.30%`, November `21.10%`)**.
* **Lead Time by Market Segment:** **Groups** book furthest ahead (`114.0` days median), followed by **Offline TA/TO (`82.0` days)** and **Online TA (`55.0` days)**, while **Direct (`15.0` days)** and **Corporate (`5.0` days)** book short-notice stays.

---

## 4. Repository Structure

```text
EDA02/
├── hotel_bookings.csv          # Source dataset (119,390 raw records)
├── hotel_booking_eda.ipynb     # Complete Jupyter Notebook (Case Study, Code, Visuals & Solution Guide)
└── README.md                   # Case Study Overview, Data Dictionary, Key Findings & Resources
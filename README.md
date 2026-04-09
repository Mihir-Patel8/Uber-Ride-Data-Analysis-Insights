# 🚗 NCR Ride Bookings — End-to-End Data Analysis

> A complete Python data analysis project on 148,767 Uber ride bookings across the
> National Capital Region (NCR), India — covering data cleaning, exploratory analysis,
> business intelligence, and actionable recommendations.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [How to Run](#how-to-run)
- [Analysis Phases](#analysis-phases)
- [Key Findings](#key-findings)
- [Business Questions Answered](#business-questions-answered)
- [Technologies Used](#technologies-used)
- [Future Work](#future-work)
- [License](#license)

---

## Project Overview

This project performs a full analytical lifecycle on a real-world ride-hailing dataset
from the NCR (Delhi, Gurgaon, Noida, and surrounding areas) covering the full calendar
year 2024. The goal is to convert raw booking records into decision-ready operational
intelligence for a ride-hailing business.

**What this project covers:**

- Data loading, validation, and type-safe cleaning
- Feature engineering (time-based features from timestamps)
- Exploratory Data Analysis (EDA) with 7+ visualisations
- Answering 10 real-world business questions with charts and interpretations
- Actionable recommendations for operations, product, and strategy teams

---

## Dataset Description

| Property | Value |
|----------|-------|
| **File** | `ncr_ride_bookings_cleaned.csv` |
| **Records** | 148,767 rides |
| **Columns** | 20 |
| **Period** | Full-year 2024 |
| **Region** | National Capital Region, India |

### Column Reference

| Column | Type | Description |
|--------|------|-------------|
| `Datetime` | datetime | Timestamp of the booking request |
| `Booking ID` | string | Unique booking identifier |
| `Booking Status` | categorical | Completed / Cancelled by Driver / Cancelled by Customer / No Driver Found / Incomplete |
| `Customer ID` | string | Anonymised customer identifier |
| `Vehicle Type` | categorical | Auto · Bike · eBike · Go Mini · Go Sedan · Premier Sedan · Uber XL |
| `Pickup Location` | string | Named pickup area within NCR |
| `Drop Location` | string | Named drop-off area within NCR |
| `Avg VTAT` | float | Vehicle Time to Arrival (minutes) |
| `Avg CTAT` | float | Customer total wait time (minutes) |
| `Cancelled Rides by Customer` | int | Flag: 1 = customer-initiated cancellation |
| `Reason for cancelling by Customer` | string | Cancellation reason (null if not applicable) |
| `Cancelled Rides by Driver` | int | Flag: 1 = driver-initiated cancellation |
| `Driver Cancellation Reason` | string | Cancellation reason (null if not applicable) |
| `Incomplete Rides` | int | Flag: 1 = ride started but not completed |
| `Incomplete Rides Reason` | string | Reason for incomplete trip |
| `Booking Value` | float | Fare in INR (null for cancelled/no-driver rides) |
| `Ride Distance` | float | Trip distance in km |
| `Driver Ratings` | float | Rating given to driver (3.0–5.0) |
| `Customer Rating` | float | Rating given to customer (3.0–5.0) |
| `Payment Method` | categorical | UPI · Cash · Uber Wallet · Credit Card · Debit Card |

### Booking Status Breakdown

| Status | Count | Share |
|--------|-------|-------|
| Completed | 92,248 | 62.0% |
| Cancelled by Driver | 26,789 | 18.0% |
| No Driver Found | 10,401 | 7.0% |
| Cancelled by Customer | 10,402 | 7.0% |
| Incomplete | 8,927 | 6.0% |

---

## Project Structure

```
ncr-ride-analysis/
│
├── NCR_Ride_Analysis.ipynb          # Main Jupyter Notebook (all 6 phases)
├── ncr_ride_bookings_cleaned.csv    # Dataset (place in same directory)
├── README.md                        # This file
│
└── outputs/                         # Generated visualisations (auto-created)
    ├── dashboard_1_operations.jpg
    └── dashboard_2_cancellation.jpg
```

---

## Installation & Setup

### Prerequisites

- Python 3.8 or higher
- pip

### 1. Clone or Download the Repository

```bash
git clone https://github.com/your-username/ncr-ride-analysis.git
cd ncr-ride-analysis
```

Or simply download and unzip the project folder.

### 2. Create a Virtual Environment (Recommended)

```bash
python -m venv venv

# Activate on Windows
venv\Scripts\activate

# Activate on macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install pandas numpy matplotlib jupyter
```

All required packages at a glance:

| Package | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥ 1.5 | Data loading, cleaning, aggregation |
| `numpy` | ≥ 1.23 | Numerical operations |
| `matplotlib` | ≥ 3.6 | All visualisations |
| `jupyter` | ≥ 1.0 | Notebook runtime |

---

## How to Run

### Option A — Jupyter Lab (Recommended)

```bash
pip install jupyterlab
jupyter lab
```

Then open `NCR_Ride_Analysis.ipynb` from the file browser.

### Option B — Classic Jupyter Notebook

```bash
jupyter notebook
```

Then open `NCR_Ride_Analysis.ipynb`.

### Option C — VS Code

1. Install the **Jupyter** extension from the VS Code marketplace.
2. Open `NCR_Ride_Analysis.ipynb` directly in VS Code.
3. Select your Python interpreter and click **Run All**.

> **Important:** Ensure `ncr_ride_bookings_cleaned.csv` is in the **same directory**
> as the notebook before running.

### Run All Cells

Once the notebook is open, use:

- **Jupyter:** `Kernel → Restart & Run All`
- **VS Code:** `Run All` button at the top of the notebook

Expected runtime: **< 2 minutes** on a standard laptop.

---

## Analysis Phases

The notebook is divided into six clearly labelled phases:

### Phase 1 — Data Loading & Understanding
- Library imports with a consistent dark visual theme
- Dataset loading with datetime parsing
- Initial inspection: `.head()`, `.info()`, `.describe()`
- Full column dictionary with types and descriptions

### Phase 2 — Data Cleaning
- Datetime parsing validation
- Time-feature engineering: `Hour`, `DayOfWeek`, `Month`, `MonthNum`, `DayNum`
- Memory optimisation via `category` dtype for low-cardinality columns
- Null value audit with structural explanation (all remaining nulls are by design)
- Duplicate booking ID verification

### Phase 3 — Exploratory Data Analysis (EDA)
Seven visualisations covering all key dimensions:

| # | Chart | Type |
|---|-------|------|
| 3.1 | Booking Status Distribution | Donut + Bar |
| 3.2 | Vehicle Type Usage & Revenue | Grouped Bar |
| 3.3 | Hourly Ride Demand | Heatmap Bar |
| 3.4 | Rides by Day of Week | Bar |
| 3.5 | Monthly Ride Volume | Area + Line |
| 3.6 | Booking Value Distribution | Histogram + Box |
| 3.7 | Driver vs Customer Ratings | Bar |

### Phase 4 — Business Questions Solved
All 10 business questions answered with dedicated visualisations
and plain-English business insights.

### Phase 5 — Future Work
Machine learning opportunities, data enrichment ideas, and
dashboard productionisation suggestions.

### Phase 6 — Conclusion
Findings summary table and 5 prioritised actionable recommendations.

---

## Key Findings

| Finding | Metric |
|---------|--------|
| Overall completion rate | **62.0%** — 38% of demand goes unfulfilled |
| Largest failure mode | **Driver cancellations at 18.0%** of all bookings |
| Peak demand hour | **18:00** with 12,298 bookings |
| Highest revenue vehicle | **Auto — ₹12.8M** (volume-driven) |
| Dominant payment method | **UPI at 45.2%** of completed rides |
| Average driver rating | **4.23 / 5.00** (uniform across all vehicle types) |
| Fare model | **~₹8–10/km + ~₹150–200 base fare** |
| Seasonal demand variance | **±5%** — essentially flat year-round |

---

## Business Questions Answered

| # | Question | Key Finding |
|---|----------|-------------|
| Q1 | Peak hours? | 17:00–19:00 window; absolute peak at 18:00 |
| Q2 | Busiest day of week? | Uniform across all days; slight weekend uptick |
| Q3 | Highest revenue vehicle? | Auto (₹12.8M) — volume, not price, drives revenue |
| Q4 | Booking completion rate? | 62% — 1 in 3 bookings fails |
| Q5 | Why do customers cancel? | Equally split: wrong address, plans changed, driver unresponsive, driver requested cancel |
| Q6 | Why do drivers cancel? | Equally split across 4 categories — no single dominant cause |
| Q7 | Monthly demand trend? | Flat with ±5% variance; no strong seasonal pattern |
| Q8 | Preferred payment method? | UPI (45%), Cash (25%), Uber Wallet (12%) |
| Q9 | Ratings by vehicle type? | All vehicle types score identically at ≈4.23 |
| Q10 | Distance vs fare relationship? | Strong positive correlation (~0.85); ₹8–10/km rate confirmed |

---

## Technologies Used

```
Python 3.8+
├── pandas       — data manipulation and aggregation
├── numpy        — numerical computing and linear regression
├── matplotlib   — all charts and dashboard visuals
└── jupyter      — interactive notebook environment
```

No external APIs, databases, or paid services required.

---

## Future Work

### Machine Learning Extensions

| Model | Goal |
|-------|------|
| Demand Forecasting | Predict hourly bookings for next 7 days |
| Cancellation Prediction | Flag high-risk bookings before dispatch |
| Dynamic Pricing | Optimise surge multiplier by zone and hour |
| Driver Churn Prediction | Identify at-risk drivers early |
| Fare Anomaly Detection | Flag potential fraud or pricing bugs |

### Data Enrichment

- **Weather data** — rainfall strongly correlates with NCR ride demand spikes
- **Traffic indices** — explains CTAT (wait time) variance
- **Geospatial coordinates** — enables zone-level heatmaps and clustering
- **Driver IDs** — enables supply-side workforce analytics

---

## Actionable Recommendations

1. **Tackle driver cancellations first** — At 18% of all bookings, this is the single
   largest revenue leak. Penalty-based policies for repeat cancellers and better
   pre-trip verification (passenger count, pickup confirmation) can materially
   improve completion rates.

2. **Staff the 17:00–20:00 window aggressively** — Evening incentives for drivers
   during peak hours will convert the highest-demand window into the highest-revenue window.

3. **Investigate "Driver Asked to Cancel" (customer-reported)** — This category
   masks driver-side behaviour; fixing it would improve both metrics simultaneously.

4. **Differentiate premium vehicle experience** — All vehicle types score 4.23 with
   no measurable quality gap. Introducing guaranteed amenities for Premier Sedan
   and Uber XL could justify premium pricing.

5. **Grow Uber Wallet share** — Wallet users are the stickiest customer segment;
   top-up cashback campaigns can increase adoption from its current 12%.

---

## License

This project is released for educational and analytical purposes.
The dataset has been anonymised — no personally identifiable information (PII) is present.

---

*Analysis conducted on 148,767 NCR ride bookings · Full-year 2024*

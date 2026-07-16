# KESCO Vehicle Tracking Dashboard (GTRAC)

A GPS-based tracking and reporting system for KESCO (Kanpur Electricity Supply Company) field vehicles. These vehicles move across Kanpur to attend to complaints such as **transformer faults, light cuts, meter faults, and other electrical issues** reported at consumer premises. This project processes raw GPS trip logs and turns them into an easy-to-read Excel dashboard so that fleet supervisors can monitor whether drivers are actually going out on duty, how much ground each vehicle is covering, and where activity is concentrated during the day.

## 📌 Purpose

KESCO maintains a fleet of service vehicles that respond to electrical faults reported by consumers or detected in the field (transformer breakdowns, meter issues, power/light cuts, etc.). This system helps answer key operational questions:

- Is a vehicle actually moving on a given day, or is it idle/parked?
- What is the average daily distance (KM) covered by each vehicle?
- During which time slots of the day are vehicles most/least active?
- Which vehicles are top performers vs. which ones show negligible movement (possible misuse or inactivity)?
- What is the longest continuous run and the farthest single trip for each vehicle?

## 📂 Repository Contents

| File | Description |
|---|---|
| `GTRAC_Updated.xlsx` | Main workbook with raw trip data, calculated summaries, and the live Dashboard sheet. |
| `Consolidated_Detail_Report.xlsx` | Raw consolidated trip log exported from the GPS tracking device/portal (source data). |

## 📊 Workbook Structure (`GTRAC_Updated.xlsx`)

### 1. Consolidated Detail Report (sheet)
Raw trip-level data, one row per vehicle trip, including:
- `Vehicle No` — Registration number of the vehicle
- `Start Time` / `Start Location` — Trip start timestamp and GPS-reversed address
- `End Time` / `End Location` — Trip end timestamp and GPS-reversed address
- `Total KM` — Distance covered in the trip
- `Running Hrs` / `Idle Hrs` — Time spent moving vs. stationary
- `Date`, `Start Decimal Hr`, `End Decimal Hr` — Normalized time fields for analysis
- `Slot 1–4` flags — Whether the vehicle was active in each time slot:
  - Slot 1: 12:00 AM – 10:00 AM
  - Slot 2: 10:00 AM – 4:00 PM
  - Slot 3: 4:00 PM – 8:00 PM
  - Slot 4: 8:00 PM – 11:59 PM
- `Distance Bucket` — Categorizes each trip as **>1 km** (genuine movement) or **≤1 km** (negligible/no movement)

### 2. Calculations (sheet)
Aggregated per-vehicle summary derived from the raw data:
- `Trips/Days`, `Total KM (All Days)`, `Daily Avg KM`
- `Avg Running Hrs (Decimal)`
- `Days >1 km` / `Days ≤1 km` — Days with genuine activity vs. near-zero movement
- `Slot 1–4 Active Days` — How many days the vehicle was active in each time slot
- `Most Continuous` — Vehicle with the longest continuous running duration
- `Longest Distance Travel` — Farthest single-day distance recorded

### 3. Dashboard (sheet)
A visual, print-ready summary built from the two sheets above, showing:
- **Fleet Daily Avg KM** — Average distance covered per vehicle per day across the fleet
- **Vehicles >1 km Today** — Count of vehicles genuinely on the move
- **Vehicles ≤1 km Today** — Count of vehicles with negligible movement (flag for follow-up)
- **Most Continuous Vehicle** — Vehicle with the longest uninterrupted run
- **Vehicles Active by Time Slot** — Bar chart of vehicle activity across the four daily time slots
- **Distance Covered Today: >1 km vs ≤1 km** — Pie chart split of active vs. inactive vehicles
- **Top 10 Vehicles by Daily Avg KM** — Table and horizontal bar chart ranking the most active vehicles

## 🚗 How It Works (Data Flow)

```
GPS Tracking Device (on vehicle)
        │
        ▼
Raw export → Consolidated_Detail_Report.xlsx
        │
        ▼
Cleaned & enriched → GTRAC_Updated.xlsx → "Consolidated Detail Report" sheet
   (adds time slots, decimal hours, distance bucket)
        │
        ▼
Aggregated → "Calculations" sheet
   (per-vehicle daily averages, active days, longest run)
        │
        ▼
Visualized → "Dashboard" sheet
   (KPIs, charts, top-10 rankings)
```

## 🛠️ Use Cases

- **Attendance/duty verification** — Confirm a driver actually went out on assigned complaint calls rather than staying parked.
- **Performance tracking** — Identify top-performing and underperforming vehicles by daily average KM.
- **Time-slot analysis** — Understand peak hours of fault-response activity (e.g., is Slot 2 the busiest for complaint resolution?).
- **Anomaly detection** — Vehicles consistently falling in the "≤1 km" bucket may indicate unreported downtime, misuse, or unassigned duty.
- **Fleet planning** — Use continuous-run and distance data to plan better vehicle allocation across zones in Kanpur.

## 📥 Data Source

Trip data is exported from the vehicle GPS tracking portal (device-based tracking, e.g., GTRAC/GPS trackers fitted to KESCO service vehicles) covering movement across various localities in Kanpur, Uttar Pradesh.

## 🔧 Requirements

- Microsoft Excel (2016 or later recommended) to view pivot-style calculations and charts.
- No external dependencies — workbook is self-contained with formulas and native Excel charts.

## 📝 Notes

- Vehicle numbers follow the UP78 series (Kanpur RTO code), e.g., `UP78GT4959`, `UP78KT8353`.
- Dates in the raw log follow `DD-MM-YYYY` format.
- The "Distance Bucket" threshold of 1 km is used as a practical cutoff to separate genuine field movement from GPS noise/idle drift.

## 📄 License

Internal use — KESCO Vehicle Tracking Project. Update this section with an appropriate license if the repository is made public.

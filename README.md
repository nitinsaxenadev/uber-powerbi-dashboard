# 🚗 Uber Analytics Dashboard — Power BI

A comprehensive **Power BI analytics dashboard** built on Uber ride data, covering booking performance, revenue trends, vehicle utilization, rider behaviour, and location-based insights — all in a single interactive `.pbix` report.

---

## 📸 Dashboard Preview

| Page | Description |
|------|-------------|
| 🏠 Home | Landing / navigation hub |
| 📊 Overview | High-level KPIs and summary trends |
| 🚙 Vehicle | Vehicle-type breakdown and performance |
| 💰 Revenue | Revenue trends by time, payment method, and customer |
| 👤 Rider | Rider segmentation and behaviour analysis |
| 📍 Location | Pickup/drop-off location intelligence |


<img width="1348" height="792" alt="Uber Dashboard" src="https://github.com/user-attachments/assets/ca52a0d9-67bf-408e-8520-65f2ea0ad9a4" />


---

## 📂 Repository Structure

```
uber-powerbi-dashboard/
│
├──INSIGHTS.md              # Key business insights and findings
├── Images.zip              # Dashboard screenshots and supporting visual assets
├── README.md               # Project documentation and component guide
├── Uber.pbix               # Power BI report file (open in Power BI Desktop)
└── Uber.xlsx               # Raw Excel dataset containing ride and booking metrics
```

---

## 📊 Report Pages & Components

### 🏠 Home
- Branded landing page with Uber logo and navigation buttons
- Acts as a page navigator to jump between report sections

---

### 📊 Overview
**KPI Cards (Top Banner)**
| Metric | Description |
|--------|-------------|
| Completed Bookings | Total successfully completed rides |
| Lost Bookings | Cancelled or failed rides |
| Booking Value | Total revenue generated |
| Total Distance | Cumulative distance across all rides |
| Avg Distance | Average distance per ride |
| Customer Rating | Aggregate customer satisfaction score |
| Driver Rating | Aggregate driver satisfaction score |





**Charts**
- 📈 **Area Chart** — Completed bookings trend over months
- 📊 **Clustered Column Chart** — Monthly completed bookings comparison
- 📊 **Clustered Bar Chart** — Booking value breakdown by vehicle type
- 🍩 **Donut Charts (×3)** — Booking status breakdown (completed vs. cancelled vs. failed)

**Slicers**
- Vehicle type filter (Advanced Slicer)
- Time period / month filter

- <img width="1347" height="792" alt="Uber overview" src="https://github.com/user-attachments/assets/673898ac-0ccd-40dc-9366-4cf1e3131cf6" />


---

### 🚙 Vehicle
**KPI Cards** — Same top-banner KPIs (dynamically filtered by vehicle)

**Charts**
- 🍩 **Donut Charts (×3)** — Booking status split per vehicle category
- 📋 **Table** — Detailed breakdown by Vehicle Type with columns:
  - Booking Value
  - Completed Bookings
  - Customer Count
  - Contribution % (`cont%`)

**Vehicle Types tracked:** UberGo, UberX, Premier, Auto, Moto, Intercity Comfort, and more.

<img width="1342" height="787" alt="Uber Vehicle" src="https://github.com/user-attachments/assets/9f1833aa-56e5-45b1-a191-eee121fd5ad6" />


---

### 💰 Revenue
**KPI Cards** — Same top-banner KPIs filtered to revenue context

**Charts**
- 📈 **Area Chart** — Revenue trend over months
- 📊 **Clustered Column Chart** — Booking value by payment method
- 📊 **Clustered Bar Chart** — Top customers by revenue
- 📊 **Clustered Bar Chart** — Revenue by vehicle type
- 🍩 **Donut Charts (×3)** — Booking status distribution

**Payment Methods tracked:** Cash, UPI, Card, Wallet, etc.


<img width="1360" height="787" alt="Uber Revenue" src="https://github.com/user-attachments/assets/3458cb36-feef-4af9-9036-41a0a239550f" />

---

### 👤 Rider
**KPI Cards** — Same top-banner KPIs + dedicated rider metrics:
- Total Unique Customers
- Return Riders
- First-Time Riders
- Regular Riders

**Charts**
- 📈 **Area Chart** — Customer count trend over months
- 🍩 **Donut Charts (×3)** — Rider segmentation (new vs. returning vs. regular)
- 📊 **Clustered Bar Chart** — Customer distribution by payment method
- 📋 **Table (Rider Detail)** — Per-customer breakdown (Booking Value, Lost/Completed rides, Avg Distance)
- 📋 **Table (Cancellations)** — Driver cancellation reasons with booking counts





**Slicer**
- Customer / Rider filter

- <img width="1343" height="781" alt="Uber Rider" src="https://github.com/user-attachments/assets/b2761e2c-c335-42ec-8c20-00d747802c20" />

---

### 📍 Location
**KPI Cards** — Same top-banner KPIs + Total Distance card

**Charts**
- 📊 **Clustered Bar Chart** — Distance covered by vehicle type
- 📊 **Clustered Bar Chart** — Top pickup locations by booking count
- 🍩 **Donut Charts (×3)** — Booking status by location segment
- 📈 **Area Chart** — Completed bookings trend by month
- 🔲 **Pivot Table** — Booking count heatmap by **Weekday × Time Slot**


<img width="1355" height="790" alt="Uber Location" src="https://github.com/user-attachments/assets/0c3beae8-1c8f-41a0-9cc5-ee610026b177" />

---

## 🗃️ Data Model

### Tables
| Table | Key Columns |
|-------|-------------|
| `Uber` | Customer ID, Vehicle Type (`Ve_Type`), Pickup Location, Drop Location, Payment Method, Customer Rating, Driver Ratings, Driver Cancellation Reason |
| `Calender` | Month, Weekday, Time Slot (date intelligence table) |
| `IMG` | Vehicle Type, Image URL (for dynamic visual icons) |
| `First Time` | Count of first-time riders |
| `_Measure` | DAX measure table |

### Key DAX Measures (`_Measure` table)
| Measure | Purpose |
|---------|---------|
| `Completed_bookings` | Count of rides with completed status |
| `Lost_bookings` | Count of cancelled / failed rides |
| `Booking_Value` | Total revenue |
| `Booking_count` | Total bookings (all statuses) |
| `Total_Distance` | Sum of all ride distances |
| `Avg_Distance` | Average distance per ride |
| `Customer_count` | Count of distinct customers |
| `Return_rider` | Count of riders with >1 booking |
| `Regular_rider` | Count of high-frequency riders |
| `cont%` | Contribution percentage of a segment |
| `Booking_Remove_Status_Failed` | Bookings removed from success count |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | Report development and data modelling |
| **DAX** | Custom measures and KPI calculations |
| **Power Query (M)** | Data transformation and loading |
| **Power BI Themes** | Custom Uber-branded colour theme (`CY26SU05.json`) |

---

## 🚀 Getting Started

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free download from Microsoft)

### Steps
1. Clone or download this repository
   ```bash
   git clone https://github.com/nitinsaxenadev/uber-powerbi-dashboard.git
   ```
2. Open **Power BI Desktop**
3. Go to **File → Open report → Browse** and select `Uber.pbix`
4. If prompted, refresh the data source by going to **Home → Refresh**
5. Use the **Home** page navigation buttons to explore each section

---

## 💡 Key Business Questions Answered

- Which vehicle types generate the most revenue?
- What are the peak booking time slots and days of the week?
- What percentage of bookings are lost (cancelled/failed)?
- Which pickup locations have the highest demand?
- How does rider retention (new vs. returning vs. regular) look?
- Which payment methods are most preferred?
- What are the top reasons for driver cancellations?

---

## 📌 Notes

- The `.pbix` file includes the **data model, queries, and visuals** all in one file
- The report uses a **custom Uber-branded theme** applied via Power BI theme JSON
- Dynamic vehicle-type icons are loaded from the `IMG` table for visual context

---

## 👤 Author

**Nitin Saxena**
Aspiring Software Developer | Data Analytics Enthusiast
[GitHub](https://github.com/nitinsaxenadev)

---

⭐ If you found this project useful, consider giving it a star!

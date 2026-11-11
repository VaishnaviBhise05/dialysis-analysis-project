# Dialysis Analytics Dashboard

**Analysis of Patient Data (Healthcare domain)**: a live, real-time dashboard and analysis toolkit for patients undergoing dialysis. It covers patient and disease patterns, chain, facility and dialysis station performance, and payment modes with the discounts and payment reductions applied to them.

> All data in this repository is **synthetic**. It contains no real patient information.

---
## Features

- **Real-time updates**: the server streams a new patient billing record every 2 seconds (Server-Sent Events), and the dashboard refreshes automatically.
- **Filters**: chain, disease and payment mode, applied to every chart, KPI and table at once.
- **KPIs**: patients, total sessions, billed amount, collected amount, discount given and discount rate.
- **Patient analysis**: patients by disease, and age group split by gender.
- **Facility, chain and station analysis**: billed vs collected per chain, and a facility table with patients, stations, sessions per station and discount %.
- **Payment and discount analysis**: payment mode share, average discount % by mode, and a monthly billed vs collected trend.
- **Auto-generated insights**: most common disease, deepest-discount payment mode, busiest and quietest facilities, and the facility with the highest discount rate.
- **CSV export** of the currently filtered records, and light/dark theme support.
- **Offline analysis script** (pandas) that writes a text report.

## Tech stack

| Layer | Technology |
|---|---|
| Backend | Python 3 standard library (`http.server`), no installs needed |
| Live feed | Server-Sent Events (`/stream`) |
| Frontend | HTML, CSS, vanilla JavaScript, [Chart.js](https://www.chartjs.org/) (loaded from CDN) |
| Analysis | pandas (optional, only for `analysis.py`) |

## Project structure

```
dialysis-analysis-project/
├── server.py            # HTTP server: static files, /api/data, /stream
├── datagen.py           # Synthetic data generator (shared by server and CSV builder)
├── analysis.py          # Offline pandas analysis -> reports/summary.txt
├── static/
│   └── index.html       # Dashboard UI
├── data/
│   └── patients.csv     # Dataset (1,400 starter records, grows while the server runs)
├── reports/
│   └── summary.txt      # Sample analysis output
├── requirements.txt
└── README.md
```

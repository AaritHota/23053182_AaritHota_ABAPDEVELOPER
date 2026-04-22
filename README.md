# SAP ABAP — Custom PO Aging ALV Report
### End-to-End ABAP Development Scenario | LearnToSAP Project 2026

![SAP](https://img.shields.io/badge/SAP-ABAP-0070F2?style=flat-square)
![Module](https://img.shields.io/badge/Module-MM%20%2F%20ABAP-14b8a6?style=flat-square)
![Report](https://img.shields.io/badge/Report-ZPO__AGING__REPORT-a78bfa?style=flat-square)

---

## 📌 Project Overview

This project demonstrates a **real-world SAP ABAP development scenario** — building a custom Purchase Order (PO) Aging Report (`ZPO_AGING_REPORT`) using ALV Grid Display. The report is one of the most commonly requested custom developments in SAP MM implementations.

The interactive web application walks through the complete development lifecycle:
- Requirement analysis and data mapping
- ABAP Dictionary structure setup (SE11)
- Selection screen design
- Database retrieval using optimised SELECT JOIN
- Data enrichment (days open + GR status)
- ALV Grid output with sorting, filtering, and totals

---

## 🚀 Features

| Feature | Description |
|---|---|
| 6-Step Process Flow | Clickable interactive walkthrough of every dev step |
| ABAP Code Viewer | Full syntax-highlighted source with one-click copy |
| Live ALV Simulator | Interactive mock ALV with filter, sort, totals, CSV export |
| DB Tables Reference | EKKO, EKPO, EKBE, MARD, LFA1, MAKT with field details |
| Error Scenarios | 4 common ABAP errors with root cause and fix |
| Interview Q&A | 5 real scenario-based interview questions with answers |

---

## 📂 Project Structure

```
sap-abap-project/
├── index.html          # Complete interactive web application (single file)
└── README.md           # This file
```

---

## 🛠 Tech Stack

| Technology | Usage |
|---|---|
| HTML5 | Structure and semantic markup |
| CSS3 | Custom design system, animations, responsive layout |
| Vanilla JavaScript | Dynamic rendering, ALV simulation, filtering |
| Google Fonts | JetBrains Mono + Syne typefaces |
| No frameworks | Zero dependencies — opens in any browser |

---

## 📋 ABAP Report: ZPO_AGING_REPORT

### Key Tables Used
- **EKKO** — Purchasing Document Header (PO Number, Vendor, Date)
- **EKPO** — Purchasing Document Item (Material, Qty, Price, Status)
- **EKBE** — PO History (Goods Receipt events — VGABE = '1')

### Report Output Fields
| Field | Source | Description |
|---|---|---|
| EBELN | EKKO | Purchase Order Number |
| LIFNR | EKKO | Vendor Code |
| BEDAT | EKKO | PO Creation Date |
| DAYS_OPEN | SY-DATUM − BEDAT | Number of days PO has been open |
| MATNR | EKPO | Material Number |
| MENGE | EKPO | Ordered Quantity |
| WEMNG | EKBE (SUM, VGABE='1') | Goods Received Quantity |
| NETPR | EKPO | Net Price per unit |

### Key Design Decisions
1. **SELECT with JOIN** over nested SELECT — avoids SELECT-in-LOOP antipattern
2. **EKBE VGABE = '1'** filter ensures only Goods Receipt events are summed
3. **REUSE_ALV_GRID_DISPLAY** with I_STRUCTURE_NAME = 'ZTY_PO' for auto field catalogue
4. **AT SELECTION-SCREEN** validation before database hit

---

## ▶️ How to Run

### Web Application
1. Download or clone this repository
2. Open `index.html` in any modern browser (Chrome / Firefox / Edge)
3. No server required — fully client-side

### In SAP System
1. Open transaction **SE38** or **SE80**
2. Create program `ZPO_AGING_REPORT`
3. Paste the ABAP source from the Code section
4. Create structure `ZTY_PO` in **SE11** with matching fields
5. Activate both objects
6. Execute via **SA38** or press **F8**

---

## 🔮 Future Improvements

- [ ] Add traffic-light ALV column (Green/Yellow/Red by days open)
- [ ] Replace LOOP+SELECT with FOR ALL ENTRIES optimisation
- [ ] Add vendor name lookup from LFA1
- [ ] Include overdue value calculation (days × net price)
- [ ] Add email alert trigger for POs older than threshold
- [ ] Extend to include open STO (Stock Transfer Orders)

---

## 👤 Author

Name- Aarit Hota
Kiit Roll no- 23053182
---

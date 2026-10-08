# Venus Pipes & Tubes Limited — MIS Reporting & Automation

Manufacturing Intelligence & Reporting system for **Production, Scrap, Machine Capacity, Job Card and Manpower Cost MIS**.

---

## 📌 Overview

This repository contains the reporting and dashboard solutions used for management information and manufacturing analysis at **Venus Pipes and Tubes Limited**.

The MIS solution is divided into two major categories:

1. **Live Power BI Reports**

   * Directly accessible through Power BI.
   * Reports are refreshed automatically.
   * Used for live production monitoring.

2. **Automation Dashboards**

   * Data is exported from the ERP Report Engine.
   * CSV/Excel files are uploaded into standalone HTML generator files.
   * The generator processes the data and builds the dashboard locally.

The overall reporting structure covers production, scrap, machine capacity, job-card performance and manpower cost.

---

## 🏢 Organization

**Venus Pipes and Tubes Limited**

### Project

**Manufacturing Intelligence & Reporting**

### Document Version

`v1.0`

### Original MIS Document

`Report MIS Document`

### Status

`Released`

---

# 📊 Reports Included

The MIS system currently contains the following reports:

| # | Report                                        | Type          | Data Source / Usage                |
| - | --------------------------------------------- | ------------- | ---------------------------------- |
| 1 | Seamless (Pipe/Tube/BA) Production Details    | Live Power BI | Power BI                           |
| 2 | Welded / L-SAW / Condenser Production Details | Live Power BI | Power BI                           |
| 3 | Job Cardwise Production Details               | Live Power BI | Power BI                           |
| 4 | Machine Capacity vs Actual Production         | Automation    | ERP → CSV → HTML Generator         |
| 5 | Scrap MIS Dashboard                           | Automation    | ERP → 4 CSV files → HTML Generator |
| 6 | Job Cardwise Production Scrap Report          | Automation    | ERP → CSV → HTML Generator         |
| 7 | Manpower Cost Report                          | Automation    | Salary Input → Generator           |

The source MIS document classifies the first three reports as live Power BI reports and the remaining four as automation dashboards.

---

# 🟦 1. Live Power BI Reports

The live reports are published in Power BI and are intended to provide continuously updated production information.

## 1.1 Seamless Production Details

**Report Name**

`Seamless (Pipe/Tube/BA) Production Details Report-Live`

**Type**

`Live – Power BI`

### Purpose

Used for monitoring production details related to:

* Seamless production
* Pipe / Tube production
* BA production
* Production performance

### Access

Open the corresponding Power BI report using the organization's authorized Power BI account.

---

## 1.2 Welded / L-SAW / Condenser Production Details

**Report Name**

`Welded_Lsaw_Condenser_Production_Details_Report-Live`

**Type**

`Live – Power BI`

### Purpose

Used for monitoring production details associated with:

* Welded production
* L-SAW production
* Condenser production

---

## 1.3 Job Cardwise Production Details

**Report Name**

`Job Cardwise_Production_Details_Report-Live`

**Type**

`Live – Power BI`

### Purpose

Used for job-card-level production monitoring and analysis.

---

# 🟧 2. Automation Dashboards

Automation dashboards are generated on demand.

The standard workflow is:

```text
ERP
 │
 ▼
ERP Report Engine
 │
 ▼
Export CSV / Excel
 │
 ▼
HTML Generator
 │
 ▼
Upload File(s)
 │
 ▼
Dashboard Generated
 │
 ├── Charts
 ├── KPIs
 ├── Tables
 └── Analysis
```

The automation dashboards use ERP Report Engine exports as their input and generate dashboards through standalone generator files.

---

# 🏭 3. Machine Capacity vs Actual Production

### Report

`Machine Capacity vs Actual Production-Automation`

### Generator

```text
Machine_Capacity_vs_Actual_Production_Generator.html
```

### Data Flow

```text
ERP
  ↓
Production Engine (Process Wise)
  ↓
R955 Machine Capacity Vs Production PBI
  ↓
CSV / Excel
  ↓
Machine Capacity Generator
  ↓
Dashboard
```

### Steps

1. Open ERP.
2. Go to:

```text
06.410.03 - Production Engine (Process Wise)
```

3. Find:

```text
R955 Machine Capacity Vs Production PBI
```

4. Open **Machine Capacity vs Actual Production**.
5. Export the report as CSV or Excel.
6. Open:

```text
Machine_Capacity_vs_Actual_Production_Generator.html
```

7. Upload the exported file.
8. The dashboard will be generated.

These steps follow the released MIS procedure.

---

# ♻️ 4. Scrap MIS Dashboard

### Report

`Scrap MIS Dashboard-Automation`

### Generator

```text
Scrap_MIS_Dashboard_Generator.html
```

### Required Input Files

The dashboard requires four CSV files:

```text
Welded.csv
Seamless.csv
Slitting.csv
Final_Cutting.csv
```

### Data Flow

```text
ERP
 │
 ├── R959 Production Summary Report-Welded
 │          ↓
 │       Welded.csv
 │
 ├── R960 Production Summary Report-Seamless
 │          ↓
 │       Seamless.csv
 │
 ├── R961 Slitting Production Summary Report
 │          ↓
 │       Slitting.csv
 │
 └── R950 Final Cutting Scrap Report-PBI
            ↓
       Final_Cutting.csv

              ↓

Scrap_MIS_Dashboard_Generator.html

              ↓

        Scrap MIS Dashboard
```

### Steps

#### Step 1 — Welded

Go to:

```text
06.400.00 - Special Engines - Production Planning
```

Find:

```text
R959 Production Summary Report-Welded
```

Select the required period and export as CSV.

Save as:

```text
Welded.csv
```

#### Step 2 — Seamless

Find:

```text
R960 Production Summary Report-Seamless
```

Select the required period and export as CSV.

Save as:

```text
Seamless.csv
```

#### Step 3 — Slitting

Go to:

```text
Slitting Plan Report
```

Find:

```text
R961 Slitting Production Summary Report
```

Export the required period as CSV.

Save as:

```text
Slitting.csv
```

#### Step 4 — Final Cutting

Go to:

```text
06.410.03 - Production Engine (Process Wise)
```

Find:

```text
R950 Final Cutting Scrap Report-PBI
```

Export the required period as CSV.

Save as:

```text
Final_Cutting.csv
```

#### Step 5 — Generate Dashboard

Open:

```text
Scrap_MIS_Dashboard_Generator.html
```

Upload:

```text
Welded.csv
Seamless.csv
Slitting.csv
Final_Cutting.csv
```

The dashboard is then generated.

The four-file input process is documented in the released MIS guide.

---

# 📝 5. Job Cardwise Production Scrap Report

### Report

`Job Cardwise Production Scrap Report-Automation`

### Generator

```text
Job Cardwise Production Scrap Report Generator
```

### Data Flow

```text
ERP
 ↓
06.410.03 - Production Engine (Process Wise)
 ↓
R957 Job Cardwise Scrap MIS-PBI
 ↓
CSV
 ↓
Job Cardwise Production Scrap Generator
 ↓
Dashboard
```

### Steps

1. Open ERP.
2. Go to:

```text
06.410.03 - Production Engine (Process Wise)
```

3. Find:

```text
R957 Job Cardwise Scrap MIS-PBI
```

4. Select the required period.
5. Export the report as CSV.
6. Open the Job Cardwise Production Scrap Report Generator.
7. Upload the CSV.
8. The dashboard will be generated.

---

# 👥 6. Manpower Cost Report

### Report

`Manpower Cost Report-Automation`

### Generator

```text
Manpower Cost Processing System
```

### Input

```text
Salary Input.xlsx
```

### Data Flow

```text
Salary Input Sheet
        ↓
Manpower Cost Processing System
        ↓
Data Processing
        ↓
Dashboard
        ↓
Excel / PDF Output
```

### Steps

1. Open the Manpower Cost Processing System.
2. Upload the salary input sheet.
3. Name the file:

```text
Salary Input
```

4. Keep only the columns specified in the reference sheet.
5. Upload the file.
6. The dashboard will be generated.
7. Download the final output as:

```text
Excel
```

or

```text
PDF
```

The released MIS document specifies the salary input workflow and Excel/PDF output capability.

---

# 📁 Suggested Repository Structure

A recommended GitHub structure is:

```text
MIS-Reporting/
│
├── README.md
│
├── PowerBI/
│   ├── Seamless/
│   ├── Welded_LSAW_Condenser/
│   └── Job_Cardwise/
│
├── Automation/
│   │
│   ├── Machine_Capacity/
│   │   └── Machine_Capacity_vs_Actual_Production_Generator.html
│   │
│   ├── Scrap_MIS/
│   │   └── Scrap_MIS_Dashboard_Generator.html
│   │
│   ├── Job_Cardwise_Scrap/
│   │   └── Job_Cardwise_Production_Scrap_Generator.html
│   │
│   └── Manpower_Cost/
│       └── Manpower_Cost_Processing_System.html
│
├── Documentation/
│   └── Report_MIS_Document.pdf
│
├── Sample_Data/
│   ├── Welded.csv
│   ├── Seamless.csv
│   ├── Slitting.csv
│   └── Final_Cutting.csv
│
└── Screenshots/
    ├── Production_Dashboard.png
    ├── Scrap_Dashboard.png
    ├── Job_Cardwise_Dashboard.png
    └── Manpower_Cost_Dashboard.png
```

> **Important:** Production data, employee/salary data, passwords, credentials, database connection strings and other confidential company information should **not** be committed to a public GitHub repository.

---

# 🔄 Overall MIS Architecture

```text
                         ┌─────────────────────┐
                         │        ERP          │
                         │  Report Engine      │
                         └──────────┬──────────┘
                                    │
                       ┌────────────┴────────────┐
                       │                         │
                       ▼                         ▼
              ┌────────────────┐       ┌─────────────────┐
              │  Live Reports  │       │ Export Reports  │
              │   Power BI     │       │ CSV / Excel     │
              └───────┬────────┘       └────────┬────────┘
                      │                         │
                      ▼                         ▼
               Live Production          HTML Generators
                 Monitoring                   │
                                              │
                         ┌────────────────────┼───────────────────┐
                         │                    │                   │
                         ▼                    ▼                   ▼
                  Machine Capacity       Scrap MIS        Job Card Scrap
                         │                    │                   │
                         └────────────────────┼───────────────────┘
                                              │
                                              ▼
                                     Management Dashboard


                    Salary Input
                         │
                         ▼
                Manpower Cost Generator
                         │
                         ▼
                    Excel / PDF
```

---

# 📋 Report Generation Matrix

| Report                  | ERP Required            | Input        | Generator | Output         |
| ----------------------- | ----------------------- | ------------ | --------- | -------------- |
| Seamless Production     | No*                     | Power BI     | Power BI  | Live Dashboard |
| Welded/L-SAW/Condenser  | No*                     | Power BI     | Power BI  | Live Dashboard |
| Job Cardwise Production | No*                     | Power BI     | Power BI  | Live Dashboard |
| Machine Capacity        | Yes                     | CSV/Excel    | HTML      | Dashboard      |
| Scrap MIS               | Yes                     | 4 CSV files  | HTML      | Dashboard      |
| Job Cardwise Scrap      | Yes                     | CSV          | HTML      | Dashboard      |
| Manpower Cost           | No ERP export specified | Salary Input | HTML      | Excel/PDF      |

`*` These reports are accessed through the published Power BI environment.

---

# 🛠️ Technology

The MIS solution uses a combination of:

* **Oracle ERP / ERP Report Engine**
* **Power BI**
* **CSV / Excel**
* **HTML**
* **JavaScript-based dashboard generators**
* **Excel / PDF reporting**

---

# 🔐 Security & Data Protection

This repository should follow strict data-security practices.

### Never commit:

```text
Passwords
API Keys
Power BI Credentials
Database Credentials
Oracle Credentials
Employee Salary Data
Personal Employee Information
Production Confidential Data
Customer Information
Connection Strings
```

Use environment variables or secure configuration wherever credentials are required.

Example:

```text
.env
config.local.js
secrets.json
```

These files should be included in `.gitignore`.

Example:

```gitignore
.env
*.env
secrets.json
config.local.js
credentials.json

# Confidential data
*.xlsx
*.xls
*.csv

# Generated reports
output/
exports/
reports/
```

---

# 🚀 Quick Start

## For Live Power BI Reports

```text
1. Open Power BI
2. Select required MIS report
3. Review latest production information
```

## For Automation Reports

```text
1. Open ERP
2. Navigate to the required Report Engine
3. Select reporting period
4. Export CSV/Excel
5. Open the corresponding HTML Generator
6. Upload the exported file(s)
7. Review dashboard
8. Export required output
```

---

# 📚 Documentation

The complete operating procedure is documented in:

```text
Documentation/Report_MIS_Document.pdf
```

The document contains:

* Report overview
* Live Power BI report references
* Automation dashboard procedures
* ERP report numbers
* CSV naming requirements
* Dashboard generation steps
* Manpower cost processing instructions

The source document is version **1.0**, dated **28 September 2026**, and marked **Released**.

---

# 👨‍💻 Ownership

**Organization:** Venus Pipes and Tubes Limited

**Project:** Manufacturing Intelligence & Reporting

**Document Owner:** Shubham Kakde

**Version:** 1.0

---

# 📈 Future Enhancements

Potential future improvements to the MIS architecture include:

* Automated ERP data extraction
* Scheduled dashboard refresh
* Centralized database storage
* Automated Power BI refresh
* Automated email distribution
* Role-based access
* Production KPI alerts
* Scrap threshold alerts
* Machine efficiency monitoring
* Historical trend analysis
* Automated Excel/PDF report distribution

---

# 📞 Support

For issues related to:

### Power BI

Verify Power BI access and report permissions.

### ERP Export

Verify the correct module, report number and reporting period.

### Automation Generator

Verify that:

* Correct CSV files are selected.
* Required file names are maintained.
* The exported data corresponds to the selected period.
* Required columns are present.

### Manpower Cost

Verify that the Salary Input file follows the required reference-sheet structure.

---

## 📌 Version History

| Version | Date              | Description                 |
| ------- | ----------------- | --------------------------- |
| 1.0     | 28 September 2026 | Initial MIS reporting guide |

---

## ⭐ Project Summary

This MIS solution provides a unified reporting framework for **manufacturing production, scrap, machine capacity, job-card performance and manpower cost analysis**.

The combination of **live Power BI reports** and **on-demand HTML automation dashboards** enables management teams to access both continuously refreshed information and flexible period-based analysis.

**Venus Pipes and Tubes Limited — Manufacturing Intelligence & Reporting**

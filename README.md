# 🧾 AuditAI — AI-Powered External Auditor

> Intelligent financial auditing system automating reconciliation, anomaly detection, and OCR invoice validation for enterprise-level audit operations.

[![Status](https://img.shields.io/badge/Status-Complete-00d1b2?style=flat-square)](https://github.com/MadyanAlammari)
[![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)](https://python.org)
[![KAU](https://img.shields.io/badge/KAU-Capstone%20Project-amber?style=flat-square)](https://kau.edu.sa)
[![Score](https://img.shields.io/badge/Audit%20Score-80%2F100-green?style=flat-square)]()
[![Match Rate](https://img.shields.io/badge/Invoice%20Match-96.6%25-brightgreen?style=flat-square)]()

---

## 📌 Overview

**AuditAI** is an intelligent AI-powered external auditing system developed as a Senior Capstone Project (CPCS499) at King Abdulaziz University. The system automates financial reconciliation and anomaly detection — replacing time-consuming manual audit procedures with an efficient, scalable, and accurate automated pipeline.

The system accepts **10 standard financial files** and performs comprehensive validation across **4 audit modules**, tested on real enterprise data.

---

## 📊 Key Results

| Metric | Result |
|--------|--------|
| Overall Audit Score | **80 / 100 (MEDIUM risk)** |
| Invoice Match Rate | **96.6%** (423/438 invoices) |
| VAT Errors Detected | **0** across 436 invoices |
| Duplicate Invoices | **0** detected |
| Missing Invoice Sequences | **0** gaps found |
| AR Reconciliation | **83.8%** (31/37 customers) |
| Processing Time | **18–32 minutes** (~4.9 sec/invoice) |
| System Completion | **98%** of planned requirements |

---

## 🏗️ System Architecture

```
Excel Files (8) + PDF Invoices (500+)
            ↓
      Data Cleaning & Column Mapping
      (Smart Column Detector — Arabic & English)
            ↓
         Audit Engine
            ↓
┌─────────────────────────────────────┐
│  Module 1: Sales Invoice Audit      │  → VAT validation, sequence gaps, duplicates
│  Module 2: Purchases Audit          │  → Same validation for purchase orders
│  Module 3: AR Reconciliation        │  → AR_Open + Sales − Receipts = AR_Close
│  Module 4: AP Reconciliation        │  → AP_Open + Purchases − Payments = AP_Close
│  Module 5: Hybrid PDF Validation    │  → pdfplumber (94.7%) + OCR fallback (5.3%)
└─────────────────────────────────────┘
            ↓
     Risk Scoring System (0–100)
            ↓
  Interactive Dashboard + Excel Reports
```

---

## ⚙️ Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.10 | Core programming language |
| Pandas | Financial data processing & reconciliation |
| NumPy | Numerical computations |
| pdfplumber | Digital PDF text extraction (primary) |
| Tesseract OCR | Scanned invoice extraction (fallback) |
| OpenCV | Image preprocessing for OCR accuracy |
| pdf2image | PDF-to-image conversion for OCR pipeline |
| Supabase | Authentication, database & backend |
| JavaScript / HTML | Interactive web dashboard |
| Tailwind CSS | Frontend UI styling |
| Google Colab | Development & testing environment |

---

## 🔍 Audit Modules

### Module 1 — Sales Invoice Audit
- VAT validation: `TotalBeforeVAT × 0.15 = VAT`
- Invoice sequence gap detection
- Duplicate invoice detection
- Total consistency checks
- **Result: 0 errors across 436 invoices**

### Module 2 — Purchases Audit
- Same validation logic applied to purchase orders
- **Result: 0 errors detected**

### Module 3 — AR Reconciliation
```
ExpectedClosing = OpeningAR + Sales − Receipts
```
- 37 customers analyzed
- 6 exceptions detected (total gap: 56,445 SAR)
- 5 exception categories: AR Mismatch, Sales Not Reflected, Receipts without Sales, Possible Advance Receipts, Balanced

### Module 4 — AP Reconciliation
```
ExpectedClosing = OpeningAP + Purchases − Payments
```
- 12 suppliers analyzed
- 8 exceptions detected (data completeness issue in source)

### Module 5 — Hybrid PDF Validation
| Method | Invoices | Percentage |
|--------|----------|------------|
| pdfplumber (Primary) | 415 | 94.7% |
| Tesseract OCR (Fallback) | 23 | 5.3% |
| **Total Processed** | **438** | **100%** |

**Match Results:**
- Full Match: 24 invoices
- Derived Match: 399 invoices
- Partial Match: 15 invoices
- Errors: 0

---

## 🎯 Risk Classification System

| Score | Risk Level | Description |
|-------|------------|-------------|
| 85–100 | 🟢 LOW | Minimal issues, data reliable |
| 65–84 | 🟡 MEDIUM | Some discrepancies, review required |
| 40–64 | 🔴 HIGH | Significant issues, immediate attention |
| 0–39 | ⛔ CRITICAL | Major failures, data unreliable |

**This company's result: 80/100 — MEDIUM**

---

## 🖥️ Web Application Features

- **Authentication** — Email/password & Google OAuth via Supabase
- **Client Management** — Add, manage, and monitor multiple companies
- **Audit Periods** — Multiple fiscal years per client
- **Document Upload** — 10 file types with validation
- **Live Dashboard** — Real-time KPIs, charts, exception tables
- **Dark/Light Mode** — Full UI theme support

---

## 🧠 Key Engineering Decisions

**Why Hybrid OCR?**
Not all invoices are digital PDFs. pdfplumber handles text-based PDFs directly (faster, more accurate), while Tesseract OCR serves as a fallback for scanned invoices — giving the system flexibility across real-world document formats.

**Why Column Mapping instead of NLP?**
Financial data is structured — fixed fields, numbers, VAT amounts. Rule-based column mapping with Arabic & English alias dictionaries is faster, more accurate, and easier to maintain than NLP for this domain.

**Why Tolerance in Matching?**
Accounting systems introduce floating-point rounding differences. A tolerance of ±1.0 SAR prevents false positives while maintaining audit accuracy.

---

## 👥 Team

| ID | Name |
|----|------|
| 2244530 | Madyan Mohammed Alammari |
| 2245434 | Yahya Salah Alwathi |
| 2244524 | Khaled Salem Tayeb |

**Supervisor:** Dr. Asaad Ahmed
**Course:** CPCS499 — Senior Project
**Institution:** King Abdulaziz University, Faculty of Computing & Information Technology
**Submission:** May 2026

---

## 🔒 Note on Source Code

Source code is **proprietary** due to use of real enterprise financial data from a client company. The full system is available for **live demonstration upon request**.

Architecture documentation and the final academic report are available in this repository.

---

## 🚀 Future Work

- Integration of Isolation Forest / Autoencoder for unsupervised anomaly detection
- Cloud integration with SAP, Oracle Financials, Zoho Books
- NLP-based intelligent audit recommendations
- Automated PDF report generation (ISA/IFRS format)
- Extended GCC language support for column detection

---

*Built with purpose. Developed at King Abdulaziz University — 2026.*

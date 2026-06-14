# 📊 Infotact Advanced Data Analytics Internship

Advanced Data Analytics project for the Infotact Technical Internship Program, focusing on Multi-Touch Marketing Attribution and SaaS Cohort Retention Analysis.


## 📅 Project 1: Multi-Touch Marketing Attribution Pipeline
**Objective:** Clean, process, and analyze 2,500+ raw marketing logs to evaluate marketing channel performance and customer conversion paths.

### 🚀 Progress Tracker
- [x] **Day 1: Data Ingestion & Initial EDA** (June 13)
  - Generated a production-scale synthetic dataset containing 2,500 records.
  - Inspected data structure and logged baseline anomalies (131 missing timestamps, 107 missing UTM sources, 200 duplicate entries).
- [x] **Day 2: Deduplication & Missing Value Resolution** (June 14)
  - Successfully dropped 200 duplicate rows caused by logging glitches.
  - Preserved critical traffic metrics by filling 107 missing `utm_source` null fields with `Organic`.
- [ ] **Day 3: Datetime Standardization & Timezone Unification** (June 15) - *Pending*
- [ ] **Day 4: Final Pipeline Export & Insights Summary** (June 16) - *Pending*


## 🛠️ Tech Stack & Tools Used
* **Language:** Python 3
* **Libraries:** Pandas, NumPy
* **Environment:** Jupyter Notebook
* **Version Control:** Git & GitHub

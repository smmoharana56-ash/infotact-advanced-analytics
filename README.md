# 📊 Multi-Touch Marketing Attribution & Data Pipeline
**Infotact Solutions Technical Internship Program** *Advanced Data Analytics — Week 1 & Week 2 Core Implementation*

---

## 📌 Project Overview
In enterprise marketing analytics, tracking absolute numbers (like total clicks) doesn't tell the full story. A marketing channel might drive thousands of site visits but fail to convert users, resulting in wasted budget. 

This project establishes an automated data cleaning, engineering, and aggregation pipeline that transforms 2,500+ raw, fragmented marketing log entries into a clean performance matrix. By resolving logging anomalies and engineering relative efficiency metrics, this pipeline allows growth teams to isolate exact channel performance and optimize marketing ROI.

---

## 📅 Week 1 & 2 Day-by-Day Implementation

### 🛠️ Phase 1: Data Ingestion & Anomaly Resolution (Week 1)
* **Day 1: Environment Setup & Raw Data Ingestion**
    * Initialized the production-scale workspace environment utilizing Pandas and NumPy.
    * Ingested the raw marketing log dataset consisting of 2,500 tracking rows.
    * Conducted baseline Exploratory Data Analysis (EDA) and cataloged critical logging glitches (200 duplicate entries, 107 missing UTM tracking fields, and 131 missing user timestamps).
* **Day 2: Deduplication & Tracking Repair**
    * Executed strict programmatic deduplication by removing 200 exact-duplicate logging rows.
    * Preserved valuable metric volumes by treating missing `utm_source` fields with a placeholder value of `'Organic'` instead of dropping rows.
* **Day 3: Timezone Unification Pipeline**
    * Handled 131 null timestamp anomalies using a chronological forward-fill (`ffill`) strategy to avoid losing conversion event history.
    * Unified mixed, fragmented string timezone offsets (EST `-05:00`, PST `-08:00`, GMT `+00:00`) into a standardized, single-clock `UTC` timeline.
* **Day 4: Time-Based Feature Engineering**
    * Parsed the clean UTC datetime structure to extract independent `click_date` and `click_hour` attributes.
    * Prepared the dataset framework to support localized hourly behavioral traffic analysis.

### 📊 Phase 2: Metrics Generation & Channel Aggregation (Week 2)
* **Day 5: Volumetric Channel Grouping**
    * Applied Pandas `.groupby()` operations on the `utm_source` attributes to condense thousands of individual visitor rows.
    * Isolated absolute channel volume counts by calculating total clicks and total conversion counts for each distinct platform.
* **Day 6: Efficiency Feature Calculation**
    * Engineered the relative efficiency metric: **Click-Through Conversion Rate (CTCR)**.
    * Normalized absolute counts into an actionable percentage index to accurately track marketing return on investment (ROI).

---

## 📐 Data Transformation & Logic Formulas

### 1. Missing Value Imputation
To maintain data integrity without skewing total volumes, null tracking identifiers are dynamically filled:
$$\text{If } utm\_source \text{ is } NaN \longrightarrow utm\_source = 'Organic'$$

### 2. Timezone Normalization
Varying global logging offsets are recalculated relative to a standard 24-hour UTC epoch:
$$\text{Timestamp}_{\text{Clean}} = \text{Timestamp}_{\text{Raw}} \pm \text{Timezone Offset} \longrightarrow \text{UTC (+00:00)}$$

### 3. Click-Through Conversion Rate (CTCR)
Calculated to evaluate the performance efficiency of individual marketing traffic sources:
$$\text{Conversion Rate (\%)} = \left( \frac{\sum \text{Total Conversions}}{\sum \text{Total Clicks}} \right) \times 100$$

---

## 🗂️ Processed Data Schema

Following the execution of the Day 1 to Day 6 pipeline, the clean master dataframe structure contains the following validated schema fields:

| Column Name | Data Type | Description | Focus Phase |
| :--- | :--- | :--- | :--- |
| `user_id` | String / Object | Unique alphanumeric string tracking an individual visitor. | Day 1 Ingestion |
| `utm_source` | String / Object | The marketing platform origin (e.g., Google, Meta, Organic). | Day 2 Cleaning |
| `timestamp` | String / Object | The original raw logging timestamp string containing mixed offsets. | Day 3 Unification |
| `clean_timestamp` | Datetime64[ns, UTC] | Standardized datetime object normalized entirely to the UTC clock. | Day 3 Unification |
| `click_date` | Date | Extracted calendar date object for daily milestone tracking. | Day 4 Feature Eng. |
| `click_hour` | Integer | Extracted hour index (0-23) for traffic peak-load analysis. | Day 4 Feature Eng. |
| `clicks` | Integer | Volumetric indicator tracking total user click-through interactions. | Day 5 Aggregation |
| `conversions` | Integer | Target flag indicator showing if a click successfully finalized a conversion. | Day 5 Aggregation |

---

## 🛠️ Tech Stack & Dependencies
* **Programming Language:** Python 3.x
* **Core Libraries:** Pandas, NumPy
* **Development Workspace:** Jupyter Notebook environment
* **Version Control:** Git & GitHub Web Interface

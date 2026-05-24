# E-Commerce Data Pipeline & Optimization

📊 **A Python data engineering pipeline that transforms raw, bloated retail data into a streamlined, high-performance dataset ready for business intelligence and analytics.**

---

## 🚀 Project Overview

Raw e-commerce datasets are frequently unorganized, featuring nested JSON fields, multi-line HTML metadata, and media links that heavily degrade database query performance. 

This project establishes a reproducible data engineering workflow using `pandas` and `numpy`. It ingests a dataset of **1,000 retail products**, executes targeted data imputation, safely removes duplicate logs, implements user-behavior simulations via mathematical broadcasting, and prunes the schema from **24 down to 7 core analytical features**[cite: 1].

### Key Achievements:
* **85% Storage Optimization:** Stripped away 17 non-essential, heavy textual/JSON columns[cite: 1].
* **No Data Loss:** Re-mapped null fields into standardized categorical metrics without altering original row logic[cite: 1].
* **Feature Engineering:** Derived absolute transaction values using uniform, seeded random volume distributions[cite: 1].

---

## 📈 System Architecture & Schema

The pipeline refines the incoming database table to isolate high-value structural metrics[cite: 1]:

| Attribute | Data Type | Key/Role | Analytical Purpose |
| :--- | :--- | :--- | :--- |
| `product_id` | `int64` | Primary Key | Unique item identifier[cite: 1] |
| `title` | `object` | Feature | Brand / Manufacturer label[cite: 1] |
| `category` | `object` | Feature | Item classification segment[cite: 1] |
| `rating` | `float64` | Feature | Customer review score (0.0 - 5.0)[cite: 1] |
| `price` | `float64` | Feature | Item unit cost in local currency (INR)[cite: 1] |
| `quantity` | `int32` | Synthetic | Simulated volume bought per transaction[cite: 1] |
| `total_amount` | `float64` | Target/Derived | Final transaction gross sales metric[cite: 1] |

---

## ⚙️ Core Pipeline Implementation Steps

The pipeline is organized sequentially across three core stages:

### 1. Ingestion & Structural Stabilization
* **Data Loading:** Ingest the raw e-commerce matrix into a standard data frame[cite: 1].
* **Null Resolution:** Address numerical gaps by defaulting missing discounts to a base layer[cite: 1].
* **Categorical Standardization:** Scan sparse qualitative blocks and map empty strings to generic tracking placeholders[cite: 1].

### 2. Feature Engineering & Vectorization
* **Deduplication:** Check unique identifiers and prune redundant rows to guarantee data integrity[cite: 1].
* **Pricing Cast:** Convert baseline pricing records into dedicated floating-point elements[cite: 1].
* **Behavioral Simulation:** Initialize a fixed random seed to generate reproducible purchase volumes per product[cite: 1].
* **Broadcasting Operations:** Compute absolute gross transaction totals using high-performance array multiplication ($price \times quantity$)[cite: 1].

### 3. Dimensionality Reduction & Persistence
* **Schema Optimization:** Apply filter parameters to retain only the high-value analytical columns[cite: 1].
* **Bloat Removal:** Drop the 17 non-essential, heavy metadata paths to clean up system memory[cite: 1].
* **Target Export:** Persist the final refined production asset as a flattened tracking file without row indices[cite: 1].

---

## 🎯 Downstream Analytical Applications

* **Dashboard Acceleration:** The lightweight file size allows instantaneous load speeds when integrated directly into Tableau, PowerBI, or Looker[cite: 1].
* **Machine Learning Ingestion:** Clean feature types and standardized numerical metrics allow immediate modeling for regression or clustering with zero pre-processing needed[cite: 1].

# 🚗 NYC Motor Vehicle Collision Data Preprocessing  
**Author:** Huizhen Jin  
**Date:** November 26, 2024  
**Project Type:** Group Project (Preprocessing Lead)  

---

## Project Overview  
This project analyzes **motor vehicle collisions** in **New York City (September 2024)**. The dataset, sourced from a publicly available traffic data repository, provides monthly updates on **collision locations, injuries, fatalities, contributing factors, and vehicle types.**  

As part of a **group project**, my responsibility was **data preprocessing**—cleaning and structuring the raw datasets for further analysis by my colleagues.  

---

## Dataset Description  
The dataset consists of **11 Excel files** (October 2024) categorized as follows:  
- **One citywide dataset (excluded due to missing information).**  
- **10 borough-level datasets**, divided into two road types:  
  1. **Highways, Bridges, and Tunnels**  
  2. **Intersections**  

Each dataset contains **two sheets**:  
- **Collision counts (location & injuries/fatalities).**  
- **Contributing factors (vehicle details & collision causes).**  

---

## Data Preprocessing Workflow  

### **1️. Data Cleaning & Standardization**  
- **Skipped unnecessary header rows** during loading to exclude notes.  
- **Fixed column name typos** (e.g., `"ColllisionKey"` → `"CollisionKey"`).  
- **Dropped irrelevant columns**, including:  
  - `OccurrencePrecinctCode`  
  - `RoadwayReferenceMarker`  
  - `RoadwayLocationDescription`  
- **Standardized Data Types:**  
  - Converted `CollisionID` & `CollisionKey` to **strings** (removing decimals).  
  - Standardized categorical values for better consistency.  
- **Handled Missing Values:**  
  - Applied a combination of **removal & imputation** based on data nature.  

### **2️. Consistency Adjustments**  
- Ensured **consistent column names** across all tables.  
- Added **borough** and **road type** columns to each dataframe.  
- Dropped extraneous **notes rows** at the end of each dataset.  

### **3️. Merging for Analysis**  
To prepare for **statistical modeling & visualization**, I merged the datasets in **three ways**:  
1. **All Collision Counts**: Aggregates all incidents across boroughs.  
2. **All Corresponding Contributing Factors**: Links factors (vehicle type, cause) to incidents.  
3. **Final Combined Dataset**: Merged both, ensuring **CollisionKey as the primary identifier**.  

---

## Challenges & Considerations  

- **Multi-Vehicle Incidents:**  
  - Each row in the **contributing factor dataset** represents **one vehicle or party involved**.  
  - Some incidents involved **multiple vehicles**, making direct aggregation challenging.  
  - ***Solution:*** Used `CollisionKey` carefully to avoid **duplicating injury counts**.  

- **Categorical Standardization:**  
  - Some datasets used different naming conventions.  
  - ***Solution:*** Applied **one-hot encoding & category mapping** where needed.  

- **Data Integrity Issues:**  
  - Several datasets had **notes mixed in table rows**.  
  - ***Solution:*** Implemented row filtering to remove these anomalies.  

---

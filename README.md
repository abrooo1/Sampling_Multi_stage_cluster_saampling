# Sampling Multi stage cluster sampling
# 📊 Ethiopia DTM Round 39 – Sampling and Site Selection (Note That the data is Not available here because of Data Protection)

This repository contains Python scripts and Jupyter notebooks for the **Displacement Tracking Matrix (DTM)** household survey sampling, site selection, and cluster allocation in Ethiopia.

---

## 🧩 Overview

The notebook automates:
- **Enumeration area–based sampling** for IDP, Returnee, Host, and Non-Displaced communities.  
- **Sample size computation** per zone using statistical formulas.  
- **Cluster allocation** and **supervisory validation planning**.  
- **Integration with GIS workflows** for enumeration area delineation and household location checks.

---

## 🧠 Methodology

### 1️⃣ Data Inputs
- `Ethiopia DTM - R39_Dataset_EC.xlsx` – main dataset of IDP sites.
- Administrative attributes:
  - Region (`M-0303`)
  - OCHA Zone and Woreda
  - Site ID / Site Name
  - Total IDP households (`M-0309`)
  - Site type (`M-0342`)

### 2️⃣ Data Processing
- Recode site types → *In Camp* vs *Out of Camp*  
- Aggregate IDP HHs by zone  
- Apply sample size formula with 90% confidence, 10% precision, design effect 1.5  
- Add 20% reserve samples  

### 3️⃣ Sampling Design
- **Average cluster size:** 17 households  
- **Sampling method:** Stratified multi-stage cluster design  
- **Outputs:**
  - Cluster count per zone  
  - Sample size per site  
  - Reserve sample size (20%)

### 4️⃣ Supervisory Sampling
- Each **Supervisor EA** covers **≥ 10 enumeration areas**.  
- Supervisors re-interview **2–3 households** already sampled by enumerators to validate responses.  
- Any GPS deviation > 100 m from the designated EA centroid is flagged in KoBoCollect.

### 5️⃣ GIS Linkages
Enumeration areas were created using:
- **WorldPop**, **Meta population**, and **Microsoft Building Footprints**
- **ArcGIS Pro Territory Design**
- EA population: **2 000 – 3 000 individuals**
- EA buildings: **300 – 700 residential**
- Sparse settlements → larger EAs  
- Dense settlements → smaller EAs

---

## 💻 Technologies Used
| Tool | Purpose |
|------|----------|
| **Python (pandas, numpy)** | Sampling logic and data aggregation |
| **ArcGIS Pro** | Enumeration area delineation and woreda segmentation |
| **Google Earth Engine** | Flood-prone area delineation and validation |
| **KoBoCollect** | Household data collection & GPS validation |
| **Power BI** | Interactive dashboard visualization |

---

## 📂 Outputs
- `Sampled_sites_Incomp and Out of Camp_r39.xlsx`
- `Main Final 150 samples.xlsx`
- `Merged sample and clusters.xlsx`

Each file contains:
- Selected sites per zone  
- Number of clusters  
- Household sample per site  
- Zone-level summary of In-Camp / Out-of-Camp populations  

---

## 🧭 Usage
1. Clone the repository  
   ```bash
   git clone https://github.com/<username>/Ethiopia_DTM_Sampling.git
   cd Ethiopia_DTM_Sampling


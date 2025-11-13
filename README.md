<h1 align="center">🏢 <b>Hong Kong Mini-Storage Data Analysis</b></h1>

<p align="center">
Exploring Hong Kong’s mini-storage market using open data, SQL, and Python.<br>
Identifying potential business opportunities for <b>Restore HK 原儲存</b>.
</p>

---

### 🎯 <span style="color:#1E90FF;">Objective</span>

- **Clean and join** facility and population datasets  
- **Calculate** facility density per 100 000 residents  
- **Visualize** district-level differences  
- **Demonstrate** SQL Anywhere-compatible queries for reporting or automation  

---

### 🧹 <span style="color:#1E90FF;">Data Cleaning Workflow</span>

| 🪜 Step | 🧩 Description |
|:--:|:--|
| 1️⃣ | Standardized district names (removed 「區」, unified spellings, merged variants like *Wanchai → Wan Chai*) |
| 2️⃣ | Joined facility + population tables by normalized district names |
| 3️⃣ | Aggregated total facilities per district |
| 4️⃣ | Calculated facilities per 100 000 residents |
| 5️⃣ | Exported clean results to CSV and SQLite DB |

**Tools used:** Python (Pandas · Regex), Google Colab Notebook, Matplotlib  

---

### 📊 <span style="color:#1E90FF;">Visualization</span>

*(Generated in Google Colab using Matplotlib)*  
![Facilities per 100 000 Population](visuals/facilities_per_100k.png)

Districts such as **Eastern**, **Central & Western**, and **Tsuen Wan** show the highest density of mini-storage facilities,  
while **Sai Kung**, **North**, and **Tai Po** remain under-served.


🔗 Open in Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rennychan/hk-mini-storage-analysis/blob/main/notebooks/HK_MiniStorage_Analysis.ipynb)


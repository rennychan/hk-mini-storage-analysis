🏢 Hong Kong Mini-Storage Data Analysis

This project analyzes open datasets from data.gov.hk
 to explore the distribution of mini-storage facilities across Hong Kong’s 18 districts and identify business opportunities for storage operators such as Restore HK 原儲存.

🎯 Objective

Clean and join facility and population datasets

Calculate facility density per 100 000 residents

Visualize district-level differences

Demonstrate SQL Anywhere–compatible queries for reporting or automation

🧹 Data Cleaning Workflow
Step	Description
1️⃣	Standardized district names (removed 「區」, unified spellings, merged variants like Wanchai → Wan Chai)
2️⃣	Joined facility and population tables by normalized district names
3️⃣	Aggregated total facilities per district
4️⃣	Calculated facilities per 100 000 residents
5️⃣	Exported clean results to CSV and SQLite DB

Tools used: Python (Pandas, Regex), Google Colab Notebook, Matplotlib

📊 Visualization

(Generated in Google Colab using Matplotlib.)

Key Observation:
Districts such as Eastern, Central & Western, and Tsuen Wan show the highest density of mini-storage facilities, while Sai Kung, North, and Tai Po remain under-served.

🔧 SQL Showcase

To demonstrate SQL proficiency, the cleaned data was loaded into a lightweight SQLite database (hk_ministorage.db) and queried directly in Google Colab.
All SQL statements are provided in sql/queries.sql
.

1️⃣ Facilities per 100 000 Residents
SELECT
  f.district,
  f.facility_count,
  p.population,
  ROUND(100000.0 * f.facility_count / p.population, 2) AS facilities_per_100k
FROM facilities_by_district f
JOIN population_by_district p
  ON p.district = f.district
ORDER BY facilities_per_100k DESC;


📄 Output: sql_result_facilities_per_100k.csv
Ranks all 18 districts by mini-storage density.

2️⃣ Top 5 Districts by Facility Count
SELECT district, facility_count
FROM facilities_by_district
ORDER BY facility_count DESC
LIMIT 5;


📄 Output: sql_result_top5.csv
Highlights the most developed storage markets (e.g. Eastern, Central & Western, Tsuen Wan).

3️⃣ Districts Below Average Density
WITH d AS (
  SELECT f.district,
         100000.0 * f.facility_count / p.population AS per100k
  FROM facilities_by_district f
  JOIN population_by_district p ON p.district = f.district
),
avgd AS (SELECT AVG(per100k) AS avg_per100k FROM d)
SELECT d.district, ROUND(d.per100k,2) AS facilities_per_100k
FROM d, avgd
WHERE d.per100k < avgd.avg_per100k
ORDER BY d.per100k ASC;


📄 Output: sql_result_below_avg.csv
Identifies under-served districts with potential for business expansion.

💡 Environment
Component	Description
DB Engine	SQLite 3 (portable; easily migrated to SQL Anywhere)
Frontend	Google Colab Notebook (HK_MiniStorage_Analysis.ipynb)
Exports	CSV outputs + Matplotlib visualization
Note	Replace LIMIT n with TOP n for SQL Anywhere syntax
🧠 Insight Summary

Eastern and Central & Western districts show the highest mini-storage density.

Tsuen Wan and Southern remain above the population-weighted average.

North, Sai Kung, and Tai Po appear under-developed, suggesting growth potential for storage operators like Restore HK.

🧰 Tech Stack

Python (Pandas · Matplotlib · Regex · CSV)

SQL (SQLite / SQL Anywhere compatible)

Google Colab / Apps Script Integration

GitHub for version control and portfolio presentation

🔗 Open in Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rennychan/hk-mini-storage-analysis/blob/main/notebooks/HK_MiniStorage_Analysis.ipynb)

GitHub for version control and portfolio presentation

🔗 Open in Colab


# 📊 SUGAR Cosmetics Social Media Performance Analysis

## 🧾 Project Overview
This project analyzes the social media performance of **SUGAR Cosmetics** to uncover insights about engagement patterns, content effectiveness, and audience behavior.  
The analysis was conducted using **Google Sheets** for cleaning, transformation, and initial visualization, followed by **Power BI** for an interactive dashboard.

---

## 📁 Files and Structure
- **Main File:** `Sugar` (Google Sheet)
- **Backup Sheet:** `Raw_Data`
- **Cleaned Sheet for Analysis:** `Cleaned_Data`
- **Exported Power BI Source File:** `Sugar_Cleaned.xlsx`

---

## 🧹 Data Cleaning & Preparation

### ✅ Columns in `Cleaned_Data`:
```
Post Date | Post Type | Campaign Type | Hashtags | Audience Emotion | Engagement Source |
Impressions | Reach | Likes | Comments | Shares | Saves | Profile Visits | Follows |
Month-Year | Weekday | Engagement Count | Engagement Rate (%) | Short Label | Hashtag Count |
Impressions_num | Reach_num | Likes_num | Comments_num | Shares_num | Saves_num |
Outlier_Flag | Check if Reach ≤ Impressions | Check negative or zero values |
Avg. for Impression | STD. Engagement | UpperThreshold | LowerThreshold |
Q1 (25th Percentile) | Q3 (75th Percentile) | IQR | Lower_Fence | Upper_Fence | Outliers
```

---

## 🧮 Formula Documentation (Google Sheets)

### **1️⃣ Derived Metrics**

| Metric | Formula | Purpose |
|--------|----------|----------|
| **Engagement Count** | `=Likes + Comments + Shares + Saves` | To measure total engagement activity per post |
| **Engagement Rate (%)** | `=(Engagement Count / Reach) * 100` | Measures engagement relative to audience reach |
| **Short Label** | `=Post Type & " - " & Campaign Type` | Combines post & campaign type for labeling |
| **Hashtag Count** | `=COUNTA(SPLIT(Hashtags, ","))` | Counts total hashtags per post |

---

### **2️⃣ Data Validation Checks**

| Check | Formula | Purpose |
|--------|----------|----------|
| **Reach ≤ Impressions** | `=IF(Reach <= Impressions, "✅", "❌")` | Ensures logical consistency |
| **Negative/Zero Values** | `=IF(MIN(Impressions, Reach, Likes, Comments, Shares, Saves) <= 0, "⚠️", "OK")` | Identifies invalid or missing data |

---

### **3️⃣ Outlier Detection (Based on Engagement Count)**

| Step | Formula | Description |
|------|----------|-------------|
| **Average Engagement (Mean)** | `=AVERAGE(Engagement Count)` | Baseline average |
| **Standard Deviation** | `=STDEV(Engagement Count)` | Data spread |
| **Upper Threshold** | `=Mean + 3 * STD` | Upper limit |
| **Lower Threshold** | `=Mean - 3 * STD` | Lower limit |
| **Q1 (25th Percentile)** | `=QUARTILE(Engagement Count, 1)` | Lower quartile |
| **Q3 (75th Percentile)** | `=QUARTILE(Engagement Count, 3)` | Upper quartile |
| **IQR** | `=Q3 - Q1` | Range between quartiles |
| **Lower Fence** | `=Q1 - 1.5 * IQR` | Detects low-end outliers |
| **Upper Fence** | `=Q3 + 1.5 * IQR` | Detects high-end outliers |
| **Outlier Flag** | `=IF(OR(Engagement Count < Lower Fence, Engagement Count > Upper Fence), "Outlier", "Normal")` | Flags anomalies |

✅ **Result:** Outliers detected = 689 (manually verified as valid promotional posts).

---

## 📊 Summary Metrics (Google Sheets)

| Metric | Value |
|--------|--------|
| Total Posts | 50,002 |
| Total Likes | 147,728,279 |
| Total Comments | 18,459,361 |
| Total Reach | 987,423,288 |
| Total Impressions | 1,276,045,750 |
| Avg. Engagement Count | 3,663.29 |
| Avg. Engagement Rate (%) | 18.54% |
| Avg. Likes per Post | 2,954.57 |
| Avg. Comments per Post | 369.19 |

---

## 📅 Trend & Category Analysis

### **Monthly Trend**
- Highest posting and engagement in **December 2024**
- Consistent engagement rate (18–19%) across months
- Positive correlation between posting frequency and engagement

### **Weekday Trend**
| Best Performing Day | Wednesday & Tuesday |
|----------------------|----------------------|
| Insight | Highest Avg. Engagement Rate (≈18.6%) on mid-week posts |
| Recommendation | Focus scheduling major campaigns mid-week |

---

## 📷 Engagement Analysis by Category

### **Post Type**
| Best Performing | Reels (18.61%) |
| Insight | Reels and Stories outperform static images |
| Recommendation | Increase Reels share by ~10–15% |

### **Campaign Type**
| Best Performing | Tutorials (18.58%) |
| Insight | Tutorials and Giveaways engage users more |
| Recommendation | Prioritize educational + incentive-driven campaigns |

### **Audience Emotion**
| Top Emotion | Curious (18.62%) |
| Insight | Curiosity-driven posts get higher interaction |
| Recommendation | Create teaser & quiz-based posts |

### **Engagement Source**
| Best Source | Collab (18.59%) |
| Insight | Collaboration campaigns perform best |
| Recommendation | Expand influencer partnerships |

---

## 📈 Power BI Dashboard Overview

### ✅ **KPI Cards**
- Total Posts  
- Total Impressions  
- Total Reach  
- Total Engagement  
- Avg. Engagement Rate (%)  
- Avg. Likes per Post  

### ✅ **Charts & Visuals**
| Visualization | Type | Title |
|----------------|------|-------|
| Monthly Trend | Combo (Bar + Line) | "Monthly Posting & Engagement Trend" |
| Weekday Analysis | Clustered Bar | "Engagement by Weekday" |
| Post Type | Combo Chart | "Post Type Performance: Engagement vs. Rate" |
| Campaign Type | Bar Chart | "Engagement by Campaign Type" |
| Audience Emotion | Donut Chart | "Engagement by Audience Emotion" |
| Engagement Source | Bar Chart | "Engagement Performance by Source" |
| Additional Chart 1 | Pie Chart | "Distribution of Posts by Campaign Type" |
| Additional Chart 2 | Donut Chart | "Engagement by Post Type" |
| Additional Chart 3 | Clustered Column Chart | "Average Engagement Rate by Emotion" |
| Additional Chart 4 | Line Chart | "Engagement Rate Trend Over Time" |

---

## 📋 Key Insights Summary
1. **Reels & Stories drive the most engagement** – optimize posting strategy for video content.  
2. **Tutorial & Giveaway campaigns** lead to higher engagement and retention.  
3. **Curiosity-driven emotions** result in higher interaction rates.  
4. **Collaborative content** (with influencers) outperforms organic posts.  
5. **Mid-week posts (Tuesday & Wednesday)** achieve the highest reach and engagement.  

---

## 🎯 Recommendations
1. Increase **video-based content (Reels/Stories)** share by 10–20%.  
2. Focus on **tutorial and giveaway** content formats.  
3. Utilize **“Curious” or “Inspired” emotional themes** in post captions.  
4. Maintain consistent posting on **Tuesdays & Wednesdays**.  
5. Leverage **influencer collaborations** for reach expansion.  

---

## ⚙️ Tools & Technologies
- **Data Source:** Google Sheets (SUGAR Cosmetics social media metrics)
- **Data Cleaning & Processing:** Google Sheets formulas
- **Visualization Tools:** Google Sheets (trend analysis), Power BI (interactive dashboard)
- **File Export:** Cleaned data → Excel (.xlsx) → Imported to Power BI

---

## 📁 Output Files
- `Sugar_Cleaned.xlsx` – Cleaned data used for Power BI
- `Sugar_PowerBI.pbix` – Power BI dashboard file
- `README.md` – Project documentation

---

## 🏁 Final Note
All data values, calculations, and visualizations were validated to ensure consistency.  
No missing values, duplicates, or invalid outliers were detected in the final dataset.  
This README serves as an end-to-end project reference for analytics, documentation, and portfolio presentation.

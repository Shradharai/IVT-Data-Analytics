# IVT (Invalid Traffic) Analytics – Internship Project

**Author:** [Shradha]  



---

## 💡 Overview

This project investigates how certain traffic patterns in mobile app advertising data can trigger fraud detection systems, resulting in IVT (Invalid Traffic) flagging. By combining feature engineering, time series analysis, anomaly detection, and visualizations, I reveal the metrics and moments that indicate suspicious activity.

---

## 📊 Dataset

- **Source:** Multi-sheet Excel file, one sheet per app (`Valid 1`, `Valid 2`, `Valid 3`, `Invalid 1`, `Invalid 2`, `Invalid 3`)
- **Scope:** Hourly records over multiple days per app
- **Sections:** “Total Data”, “Daily Data”, “Hourly Data” – *Analysis focuses exclusively on Hourly Data.*

### Features (Columns)

| Feature             | Description                                                                    |
|---------------------|--------------------------------------------------------------------------------|
| Date Or Hour        | Hourly timestamp of the aggregated data                                        |
| unique_idfas        | Unique device identifiers (IDFAs) observed                                     |
| unique_ips          | Unique IP addresses in traffic                                                 |
| unique_uas          | Count of unique user-agent strings detected                                    |
| total_requests      | Total ad requests from all devices during the hour                             |
| requests_per_idfa   | Average requests per device (can flag automation if abnormally high)           |
| impressions         | Ads successfully rendered (checks delivery integrity)                          |
| impressions_per_idfa| Ads delivered per device                                                       |
| idfa_ip_ratio       | Unique devices / unique IPs (high = cluster/proxy use)                         |
| idfa_ua_ratio       | Unique devices / unique user-agents (high = device spoofing or botnets)        |
| IVT                 | Invalid Traffic score (target for fraud/automation detection)                  |

---

## 🔬 Analytical Steps

1. **Data Loading & Cleaning:**  
   - Extracted hourly data from each app sheet.
   - Standardized, parsed, and cleaned all feature columns for robust analysis.

2. **IVT Time Series Visualization:**  
   - Plotted IVT scores over time for each app, instantly revealing the “healthy vs. suspicious” division between valid and invalid apps.

3. **Trigger Event Analysis:**  
   - Identified the precise hour and feature values where IVT first became nonzero for each app.
   - Compared these values to establish what really triggered the IVT flag.

4. **Correlation & Outlier Detection:**  
   - Computed correlations for all features vs. IVT.
   - Created scatterplots of key features, colored by IVT, to visually spot anomalies and sharp transitions.

5. **Reporting:**  
   - Summarized results, patterns, and recommendations in a clear, technical report.
   - Included actionable steps for future monitoring and fraud prevention.

---

## 📈 Results Highlight

- **Valid apps**: Never exhibited dangerous spikes in feature metrics or IVT; traffic was organic and stable.
- **Invalid apps**: IVT jumped sharply at certain hours, exactly when metrics like `idfa_ua_ratio`, `unique_uas`, and `requests_per_idfa` also surged.
- **Visualization and statistics together**: Provided a fast blueprint for detecting risky traffic *before* fraud becomes a systemic problem.

---

## 🛠 Repo Usage & Structure

**To reproduce the analysis:**
1. Place `Data-Analytics-Assignment.xlsx` in your project folder.
2. Open `ivt_analysis.ipynb` (Python/Jupyter Notebook) and run all cells.
3. Review the generated plots and review the attached report (`IVT_Traffic_Report.pdf`).


---

## 📋 Recommendations

- Proactive monitoring of `idfa_ua_ratio`, `unique_uas`, and `requests_per_idfa` is essential for any live ad platform.
- Use valid-app feature benchmarks to set dynamic thresholds, and trigger reviews on outlier detection.
- Integrate time series and scatterplot dashboards into analyst toolkits for rapid fraud response.

---

## 📬 Contact & License

This project was conducted as part of an internship analytics evaluation.  
For permissions or collaboration, contact: [your email]

---

*If you found this analysis insightful, please ⭐ star or fork the repository for future reference!*


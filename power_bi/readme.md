# 📊 Power BI Reporting & Advanced UX Dashboard

This directory contains the final presentation layer of the Multi-Property GA4 Analytics Pipeline. The interactive dashboard translates the transformed data outputted by the Python ETL scripts into actionable, high-level business insights tailored for digital marketing and portfolio management.

*Note: To ensure confidentiality and protect sensitive business assets, all data presented in this portfolio dashboard has been altered and randomized. The numbers and trends do not reflect actual real-world web traffic.*

## 🌐 Interactive Dashboard

You can explore the fully interactive version of the dashboard online:    
👉 **[View the Interactive Report](https://mavenshowcase.com/project/56439)**

You can find all the DAX measures used here:    
👉 **[View the DAX code](dax_code.csv)**

---

## 💡 Key Features & Analytical Capabilities

* **Executive KPI Banner:** Tracks core web metrics including Active Users, New Users, Sessions, Engagement Rate, and User Engagement Duration, complete with dynamic Year-over-Year (YoY) performance indicators.
* **Dynamic Metric Toggling (Bookmarks):** An interactive sidebar menu allows users to switch the report view between the 5 core metrics. This approach utilizes Bookmarks to perfectly preserve distinct Y-axis formatting (e.g., percentages vs. `HH:MM:SS` duration formats) across different views.
* **Contextual Tooltips (Deep-Dives):** Custom Report Page Tooltips provide context on demand.
* **Domain-Level Segmentation (Page 2):** A dedicated deep-dive page allowing for granular comparison of performance and acquisition channels across the different websites within the portfolio.

---

## 🧮 DAX Implementation Highlights

The report relies on a centralized `_Key Measures` table, keeping the data model clean. Key DAX implementations include:

* **Custom Time Intelligence ("Latest Data State"):** Instead of standard functions like `SAMEPERIODLASTYEAR`, the report uses `VAR` and `MAX('Calendar'[Year])` logic. This ensures the dashboard automatically defaults to the most recent available year in the dataset, providing a robust viewing experience even with incomplete data.
* **Dynamic Threshold Indicators:** Custom logic utilizing `SWITCH` and `UNICHAR` (▲/▼) to generate green/red YoY arrows. A sensitivity threshold ensures arrows only appear for practically significant thresholds, reducing data noise.
* **Robust Ratios & Formatting:** Extensive use of the `DIVIDE` function for safe zero-denominator handling, and complex formatting string logic to display total seconds as readable `HH:MM:SS` durations.

---

## 📸 Dashboard Preview

*(A static snapshot of the main Executive Summary page)*
![Power BI Main Dashboard Preview](../docs/report_preview_first_page.png)

*(A static snapshot of the Deep-Dive View page)*
![Power BI Deep-Dive page Preview](../docs/report_preview_second_page.png)
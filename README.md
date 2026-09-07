# Smart Business Analytics and Decision Support System for Bommi Samayal

## Project Overview
Micro-enterprises in the food and beverage industry frequently rely on intuition rather than data, which often results in operational inefficiencies, stock-outs, and pre-consumer food waste. Furthermore, existing commercial Point of Sale (POS) systems are typically expensive, overly complex for small stall vendors, and fail to incorporate external variables such as weather forecasts into their reporting. 

This project delivers a highly accessible, mobile-optimized Business Intelligence (BI) dashboard tailored specifically for "Bommi Samayal," a local food stall. Built upon the Technology Acceptance Model (TAM) for maximum user-friendliness and Data-Driven Decision Making (DDDM) theory, this decision support system empowers micro-vendors to transition from guesswork to evidence-based inventory forecasting and staff scheduling.

## Dashboard Preview
![Bommi Samayal Dashboard](<Images/Screenshot 2026-08-04 095735.png>)

## Data Architecture & Methodology
The backend architecture is structured around a traditional Business Intelligence Extract, Transform, Load (ETL) pipeline, designed to process batch data efficiently.

### 1. Data Ingestion & ETL
* **Data Sources:** The system aggregates historical POS transactional data (exported as CSV files) with external local weather data[cite: 4].
* **Transformation:** Microsoft Excel and Power Query were utilized to clean the raw data. This involved standardizing 24-hour time formats, isolating blank fields, removing duplicates, and correcting manual data entry errors (e.g., standardizing misspelled items like "Nsi Lemak" to "Nasi Lemak").

### 2. Data Modeling
* The analytical engine utilizes a **Star Schema** relational database design to optimize query speeds and ensure instantaneous dashboard filtering.
* **Fact Table:** `Fact_Sales` serves as the central table containing numerical transactional metrics, such as Price, Quantity, Time, and custom Data Analysis Expressions (DAX).
* **Dimension Tables:** Four surrounding dimension tables (`Dim_Menu`, `Dim_Environment`, `Dim_Date`, and `Dim_Customer`) provide descriptive context to the transactional data.

## Core Features & Interface Design
The user interface adheres to a "mobile-first" philosophy, utilizing high-contrast visuals, minimalistic charts, and vertical scrolling to reduce cognitive load for busy vendors.
* **Executive KPI Summary:** The top tier of the dashboard displays immediate health metrics: Total Revenue, Total Orders, Average Ticket Size, and the percentage of Dine-in vs. Takeaway orders.
* **Weather & Demand Forecasting:** A 100% Stacked Column chart correlates daily weather conditions with customer purchasing behavior, visually demonstrating the shift between dine-in and takeaway preferences.
* **Time & Demographics View:** Area and donut charts map out the busiest operating hours alongside customer gender distributions.
* **Interactive Slicers:** Dynamic cross-filtering allows the user to isolate specific variables (e.g., viewing only "Rainy" Fridays) to recalculate all visual metrics instantly.

## Key Business Insights
The deployment of this dashboard revealed several actionable insights that directly influenced Bommi Samayal's daily operations:
* **Hourly Demand Surges:** The stall experiences its most significant customer traffic at precisely 18:00 (6:00 PM) and 21:00 (9:00 PM), allowing the vendor to align staff schedules with peak rushes.
* **Top-Moving Inventory:** Various iterations of Nasi Lemak were mathematically identified as the consistent best-sellers, ensuring the vendor prioritizes bulk procurement of core ingredients like rice and sambal to avoid stock-outs.
* **Weather-Driven Consumer Behavior:** Environmental data proved to heavily dictate dining choices; on sunny days, dine-in orders account for roughly 80% of sales. 
* **Operational Pivot:** Conversely, during rainy weather, takeaway orders spike to nearly 80%, prompting the vendor to proactively prepare takeaway packaging inventory based on morning weather forecasts.

## Future Scope
To further evolve this proof-of-concept into a fully automated enterprise solution, future development phases will include:
* **Custom Mobile POS Application:** Digitizing the manual logbook into a tablet-based checkout app.
* **Real-Time Cloud Integration:** Connecting the POS app to a live cloud database (e.g., Firebase or AWS) to enable real-time dashboard streaming via API.
* **Cost Analytics:** Expanding the data model to include ingredient cost variables, upgrading the dashboard from tracking Gross Revenue to calculating Net Profit margins.

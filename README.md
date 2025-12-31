# Online Retail Analytics – Data Mining & Visualization Project

## Project Overview

This project applies **data mining and visualization techniques** to an online retail dataset covering transactions from **December 2010 to December 2011**.  
The goal is to extract **actionable business insights** related to customer behavior, product performance, revenue optimization, and sales trends, using the **CRISP-DM methodology**.

The project was completed as part of the **Data Mining & Visualization Workshop Project**, under the guidance of **Dr. Lydia Bouchlaghem**.

---

## Business Context

The dataset represents a **UK-based online retail company** selling gift items and home goods to both **B2C and B2B customers**, with operations spanning **38 countries**.  
The business seeks to better understand:

- Customer purchasing behavior
- Product bundling opportunities
- Seasonal sales trends
- Revenue drivers across customers, products, and regions
- Overall data quality and readiness for analytics

---

## Methodology: CRISP-DM

The project strictly follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework:

1. Business Understanding  
2. Data Understanding  
3. Data Preparation  
4. Modeling  
5. Evaluation  

Deployment is outside the scope of this academic project.

---

## Phase 1 – Business Understanding

### Business Objectives (SMART)

1. **Customer Segmentation**  
   Identify the top customer segments based on purchasing behavior and provide targeted marketing recommendations aimed at improving customer retention.

2. **Product Bundling Insights**  
   Identify the most frequently co-purchased product pairs to support upselling and promotional strategies.

3. **Sales Trend Analysis**  
   Analyze seasonal sales and revenue patterns to support inventory planning.

4. **Revenue Optimization Insights**  
   Identify key revenue drivers across customers, products, and regions.

5. **Data Quality Improvement**  
   Perform a full data quality assessment to ensure the dataset is fully ready for modeling.

### Success Criteria

- At least **3 meaningful customer segments**
- Clear, interpretable visualizations
- Actionable business recommendations
- Clean, reproducible analytical pipeline

---

## Phase 2 – Data Understanding

### Dataset Summary

- **Time period:** December 2010 – December 2011  
- **Transactions:** ~500,000  
- **Customers:** ~4,000 unique  
- **Products:** ~4,000  
- **Countries:** 38  

### Key Observations

- Missing `CustomerID` values (~25%)
- Cancelled transactions (InvoiceNo starting with `C`)
- Negative quantities (returns)
- Zero unit prices (very rare)
- Highly skewed monetary values
- Revenue concentrated in a small number of customers and products

---

## Phase 3 – Data Preparation

This phase ensured the dataset was **clean, consistent, and analytically ready**.

### Data Cleaning

- Removed records with missing `CustomerID`
- Separated cancelled transactions into `df_cancelled`
- Retained completed transactions in `df_completed`
- Removed zero `UnitPrice` records
- Handled outliers using robust methods

### Feature Engineering

#### Order & Revenue Features
- `OrderValue = Quantity × UnitPrice`
- `CLV` (Customer Lifetime Value)
- `OrderSizeCategory` (Small / Medium / Large)

#### Time-Based Features
- Date, Year, Month, Day
- MonthName
- Weekday
- IsWeekend
- Hour and Minutes

#### Customer Segmentation Features
- Recency
- Frequency
- Monetary

#### Geographic Features
- Country
- Engineered `Region` feature (used instead of city)

---

## Phase 4 – Modeling (Customer Segmentation)

### RFM Modeling

- Computed **Recency, Frequency, Monetary (RFM)** metrics at customer level
- Applied **log transformation** to handle skewed distributions
- Scaled features using **RobustScaler**
- Applied **PCA** for visualization

### Clustering

- Used **K-Means clustering**
- Evaluated multiple values of K using the elbow method
- Final selection: **K = 4**

### Segment Mapping (Business Logic)

Clusters were mapped to business segments using **data-driven ranking logic**:

- **Champions** – Recent, frequent, high spenders
- **Loyal Customers** – Frequent and consistent buyers
- **At Risk** – Declining engagement
- **Hibernating** – Long inactive, low value

Segment labels were attached to both:
- `rfm` dataframe
- `df_completed` dataframe

---

## Phase 5 – Evaluation

Phase 5 focused on **evaluating the segmentation model**, not redoing upstream analysis.

### Model Evaluation

- Cluster size distribution reviewed
- PCA visualization used to assess separation
- Segment-level RFM statistics analyzed for interpretability

### Business Evaluation

Each segment was evaluated against business objectives:

| Segment | Key Traits | Recommended Actions |
|------|-----------|--------------------|
| Champions | High value, frequent, recent | Loyalty rewards, VIP offers |
| Loyal Customers | Regular buyers | Cross-sell, upsell |
| At Risk | Reduced activity | Re-engagement campaigns |
| Hibernating | Long inactive | Win-back or minimal effort |

### Success Criteria Validation

- ✅ At least 3 meaningful customer segments achieved
- ✅ Clear behavioral differences across segments
- ✅ Actionable insights for marketing and sales
- ✅ Clean and reproducible analysis pipeline

---

## Visualizations Included

- Sales over time (monthly revenue trends)
- Top products by revenue
- Regional and country-level revenue distribution
- Order value and RFM distributions
- PCA-based cluster visualization
- Segment-level KPIs

Each visualization is tied to a **specific business question**.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn / Plotly
- Scikit-learn

---


---

## References

- Bouchlaghem, L. (2025). *Data Mining & Visualization Workshop Project: Course Guide.* ECE Paris, MSc 2 AI Project Guide Material.
- Kasem, M. S. E., et al. (2024). Customer profiling, segmentation, and sales prediction using AI in direct marketing. *Neural Computing and Applications*.
- Wilbert, H. J., et al. (2023). Recency, Frequency, Monetary Value, Clustering, and Internal and External Indices for Customer Segmentation from Retail Data. *Algorithms, 16(9)*.

---

## Author

**Uduma Idika**  
MSc Artificial Intelligence  
ECE Paris

---

## Final Note

This project demonstrates a **complete CRISP-DM workflow**, combining strong data preparation, sound modeling decisions, and business-focused interpretation.  
All analyses are reproducible and aligned with real-world retail decision-making.




# 🏥 India Public Health Infrastructure & Disease Burden Analysis

## 📌 Project Overview

This project performs a comprehensive analysis of public health
infrastructure and disease burden across 36 Indian states and UTs
using NFHS (National Family Health Survey) data.

Three analytical approaches are combined:
- Data Analysis — 18 visualisations covering health indicators
  across all states including IMR, anaemia, stunting, immunization
- Machine Learning — K-Means clustering to classify states into
  health tiers, with Random Forest and XGBoost classification
- Geospatial Visualisation — interactive Folium map showing
  health tier of every Indian state

---

## 📂 Project Structure

```
health-infrastructure-india/
├── data/
│   ├── health_merged_clean.csv
│   ├── health_merged_with_score.csv
│   └── state_health_tiers.csv
├── notebooks/
│   └── india_health_infrastructure_analysis.ipynb
├── outputs/
│   ├── chart1_health_score.png
│   ├── chart2_imr_states.png
│   ├── chart3_institutional_delivery.png
│   ├── chart4_child_anaemia.png
│   ├── chart5_immunization.png
│   ├── chart6_stunting.png
│   ├── chart7_correlation_heatmap.png
│   ├── chart8_beds_vs_imr.png
│   ├── chart9_sanitation_vs_stunting.png
│   ├── chart10_delivery_vs_anaemia.png
│   ├── chart11_top5_vs_bottom5.png
│   ├── chart12_health_score_distribution.png
│   ├── chart13_elbow.png
│   ├── chart14_pca_clusters.png
│   ├── chart15_cluster_heatmap.png
│   ├── chart16_model_comparison.png
│   ├── chart17_feature_importance.png
│   ├── chart18_shap.png
│   ├── india_health_tier_map.html
│   ├── model_comparison.csv
│   ├── model_random_forest.pkl
│   ├── model_xgboost.pkl
│   └── model_logistic_regression.pkl
└── README.md
```

---

## 📊 Dataset

| Dataset | Source | Coverage |
|---|---|---|
| NFHS-4 Health Indicators | Kaggle / MoHFW | 36 States/UTs |
| Hospital Beds State-wise | Kaggle | 36 States/UTs |

**Key Indicators Used:**

| Indicator | Type | Description |
|---|---|---|
| IMR | Negative | Infant Mortality Rate per 1000 births |
| U5MR | Negative | Under-5 Mortality Rate per 1000 births |
| Institutional Delivery | Positive | % births in health facilities |
| Full Immunization | Positive | % children fully immunized |
| Child Anaemia | Negative | % children 6-59 months anaemic |
| Women Anaemia | Negative | % women 15-49 years anaemic |
| Stunting | Negative | % children under 5 stunted |
| Underweight | Negative | % children under 5 underweight |
| Clean Water | Positive | % households improved water source |
| Sanitation | Positive | % households improved sanitation |
| Electricity | Positive | % households with electricity |
| Clean Fuel | Positive | % households using clean cooking fuel |
| ANC 4+ Visits | Positive | % mothers with 4+ antenatal visits |
| Total Beds | Positive | Total hospital beds per state |

---

## 💯 Composite Health Score

A Composite Health Score (0–100) was calculated for every state
by normalising all 14 indicators and combining them equally.

Positive indicators contribute directly.
Negative indicators are inverted so that higher always means better.

This single score enables fair cross-state ranking and clustering.

**Results:**
| Rank | State | Health Score |
|---|---|---|
| 1 | Kerala | 89.92 |
| 2 | Goa | 85.98 |
| 3 | Puducherry | 81.32 |
| ... | ... | ... |
| 34 | Uttar Pradesh | 28.00 |
| 35 | Jharkhand | 27.94 |
| 36 | Bihar | 24.10 |

---

## 🔍 Key EDA Findings

### 1. Extreme Inter-State Disparity
Kerala scores 89.92 while Bihar scores 24.10 on the same
composite index — a gap of 65 points on identical indicators.
India's health challenge is not uniform — it is concentrated
in specific states requiring targeted intervention.

### 2. IMR and Institutional Delivery Link
States with IMR above 40 consistently show institutional
delivery below 70%. The data confirms that every 10%
increase in institutional delivery correlates with
measurable reduction in infant mortality.

### 3. Anaemia is Universal
Child anaemia above 50% is found across states of all
health tiers — including relatively developed states.
This confirms anaemia is not a poverty problem alone
but a nutrition system failure cutting across all levels.

### 4. Sanitation Drives Stunting
States with sanitation coverage below 40% show stunting
rates above 40% in almost every case. Clean sanitation
is the single most consistent predictor of child nutrition
outcomes across all 36 states.

### 5. Hospital Beds vs Mortality
States with fewer hospital beds per population consistently
show higher IMR. Infrastructure investment directly
correlates with survival outcomes.

---

## 🤖 Machine Learning

### K-Means Clustering — Health Tier Classification

States clustered into 4 tiers using 9 health indicators:

| Tier | Color | Characteristics |
|---|---|---|
| 🟢 Strong | Green | High delivery, immunization, low mortality |
| 🔵 Moderate | Blue | Above average on most metrics |
| 🟠 Developing | Orange | Mixed — specific gaps in some indicators |
| 🔴 Critical | Red | High mortality, low coverage across metrics |

### Classification Models

| Model | Accuracy |
|---|---|
| Logistic Regression | 0.5556 |
| Random Forest | 0.7778 |
| XGBoost | 0.5556 |


### Feature Importance
Random Forest and SHAP analysis identify which indicators
most strongly predict a state's health tier — enabling
evidence-based prioritisation of interventions.

---

## 🗺️ Interactive Map

Interactive Folium map shows health tier for every Indian state.

Download and open locally:
```
outputs/india_health_tier_map.html
```

Hover over any state to see its name.
Color shows health tier instantly.

---

## 📋 What Each Health Tier Means and What Should Be Done

### 🟢 Strong States
Strong health infrastructure across all indicators.
- Shift focus from coverage to quality of care
- Invest in non-communicable disease prevention
- Use as model states — study their systems for replication
- Focus on urban health inequality within these states

### 🔵 Moderate States
Above average but with specific indicator gaps.
- Identify the 2-3 lagging indicators per state
- Strengthen secondary care infrastructure
- Improve nutrition programme reach
- Increase ANC quality not just quantity

### 🟠 Developing States
Mixed performance — strong in some areas, weak in others.
- Priority push on immunization and institutional delivery
- Invest in clean water and sanitation infrastructure
- Deploy more community health workers in rural areas
- Strengthen cold chain for vaccine delivery

### 🔴 Critical States
Comprehensive health system failure across indicators.
- Emergency focus on reducing IMR and U5MR
- Rapid expansion of PHC and CHC infrastructure
- Increase hospital beds per 1000 population urgently
- Child anaemia and stunting intervention at scale
- Increase female health workers in rural blocks
- Improve maternal nutrition during pregnancy
- Strengthen institutional delivery incentive programmes

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Python | Core programming |
| Pandas | Data cleaning and manipulation |
| NumPy | Numerical operations |
| Matplotlib + Seaborn | All visualisations |
| Scikit-learn | K-Means clustering, classification, PCA |
| XGBoost | Classification model |
| SHAP | Model explainability |
| Folium | Interactive health tier map of India |
| Google Colab | Development environment |

---

## 🚀 How to Run

1. Open notebook in Google Colab:
   `notebooks/india_health_infrastructure_analysis.ipynb`

2. Upload datasets from `data/` folder

3. Run all cells top to bottom

4. Open `outputs/india_health_tier_map.html`
   in any browser to view the interactive map

---

## 💡 Key Takeaways

- A composite health score enables fair cross-state comparison
  beyond any single indicator
- Sanitation and institutional delivery are the two strongest
  predictors of child health outcomes across India
- Anaemia is a universal challenge not limited to
  the least developed states
- Inter-state health disparity in India is extreme —
  targeted state-specific interventions outperform
  uniform national programmes
- Physical infrastructure matters but quality and
  utilisation of existing facilities matter equally

---

## 📁 Author

**Ishika Khapekar**


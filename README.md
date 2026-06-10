# ✈️ Customer Behavior in an Airline Loyalty Program

**Author:** Sabrina Giselle Gómez Trujillo

Exploratory and statistical analysis of a Canadian airline's loyalty program. Using two complementary datasets, the project examines members' sociodemographic profile, flight behavior, and points usage, with the goal of identifying business opportunities and laying the groundwork for CLV and churn predictive models.

---

## 📁 Repository Structure

```
.
├── data/
│   ├── Customer Flight Activity.csv      # Monthly flight activity per member
│   └── Customer Loyalty History.csv      # Customer profile and membership history
├── Airline_Loyalty_Analysis.ipynb        # Main notebook
└── README.md
```

---

## 📊 Datasets

| Dataset | Records | Variables | Content |
|---|---|---|---|
| `Customer Flight Activity.csv` | 405,624 | 10 | Booked flights, distance, points accumulated and redeemed |
| `Customer Loyalty History.csv` | 16,737 | 16 | Customer profile, province, education, income, card type |

The datasets are joined via a **LEFT JOIN** on `Loyalty Number`, resulting in a combined dataset of **401,688 records** after cleaning.

---

## 🛠️ Tools & Libraries

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![pandas](https://img.shields.io/badge/pandas-✓-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-✓-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-✓-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-✓-4c72b0)
![SciPy](https://img.shields.io/badge/SciPy-✓-8caae6?logo=scipy)
![statsmodels](https://img.shields.io/badge/statsmodels-✓-3c6478)

---

## 🗂️ Notebook Structure

| Section | Content |
|---|---|
| **0 · Setup** | Imports, global configuration and data loading |
| **1 · Exploration & Cleaning** | Initial EDA, duplicates, nulls, imputation and dataset join |
| **2 · Statistical Analysis** | Descriptive stats, outliers (IQR), correlations and categorical variables |
| **3 · Visualization** | Seven key charts with business interpretation |
| **4 · Hypothesis Testing** | ANOVA and Kruskal-Wallis: booked flights by education level |
| **5 · Conclusions** | Key findings and strategic next steps |

---

## 🔍 Key Findings

| # | Finding | Implication |
|---|---|---|
| 1 | **75% of members never redeem points** | Benefits program is underutilized — high activation opportunity |
| 2 | **Aurora card generates 43% more CLV** than Star | Promoting tier upgrades is the highest-impact profitability lever |
| 3 | **Clear seasonality**: peaks in summer and December | Plan loyalty campaigns and capacity for peak season |
| 4 | **12.35% of members cancelled**, with CLV ~15% below average | Churn model is feasible and necessary for early retention |
| 5 | **Ontario + BC + Quebec = 78%** of members | Segment regional campaigns; special personalization for Quebec |
| 6 | **Points policy change in 2018**: higher pts/km slope | Include `Year` as a control variable in points models |
| 7 | **Education level does not predict flights** (ANOVA p = 0.49, Kruskal-Wallis p = 0.45) | Booking campaigns can be designed without education segmentation |
| 8 | **Redundant variables identified**: `Total Flights`, `Dollar Cost Points Redeemed` | Reduce dimensionality before modeling |

---

## 📈 Visualizations

1. **Booking seasonality** — monthly comparison 2017 vs 2018
2. **Distance vs points accumulated** — program consistency check by year and loyalty card tier
3. **Geographic distribution** — unique customers by province
4. **Salary by education level** — coherence validation and salary gap
5. **Distribution by card type** — penetration per tier and associated median CLV
6. **Demographic profile** — marital status and gender of members
7. **CLV distribution** — histogram + KDE showing skewness and high-value segment

---

## 🔬 Hypothesis Testing

**Question:** Does the number of booked flights differ significantly by customer education level?

| Test | Statistic | p-value | Conclusion |
|---|---|---|---|
| ANOVA | F = 0.8564 | 0.4893 | Not significant |
| Kruskal-Wallis | H = 3.6735 | 0.4520 | Not significant |

No statistical evidence of differences in flight activity by education level. Means are virtually identical across groups (98.7–101.0 flights per customer). Variables with greater discriminating power are `Loyalty Card`, `Province`, and `CLV`.

---

## 🚀 Next Steps

1. **CLV prediction model** — using `Loyalty Card`, `Province`, `Education`, `Marital Status`, `Salary` and flight activity as features.
2. **Churn model** — binary classifier with `Cancelled` as the target variable.
3. **Customer segmentation** — clustering (K-Means or hierarchical) on activity and sociodemographic profile.
4. **Tier upgrade analysis** — identify the profile of members who upgraded tiers to replicate the pattern through targeted campaigns.
5. **A/B experiment** — points activation campaign for the 75% of members who never redeem.

---

## ▶️ How to Run

1. Clone the repository and navigate to the root folder.
2. Make sure the data files are in the `data/` folder.
3. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels
   ```
4. Open the notebook:
   ```bash
   jupyter notebook Airline_Loyalty_Analysis.ipynb
   ```
¿
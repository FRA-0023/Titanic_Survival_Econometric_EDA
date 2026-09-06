# 🚦 Titanic Survival Dynamics: An Econometric & Spatial EDA

[![Language](https://img.shields.io/badge/Language-R%204.4-276DC3?style=flat&logo=r)](https://www-r-project.org/)
[![Framework](https://img.shields.io/badge/Framework-tidyverse%20%7C%20ggplot2-blue)](https://www.tidyverse.org/)
[![Report](https://img.shields.io/badge/Report-20--Page%20Executive%20PDF-red?logo=adobeacrobatreader)](Titanic.pdf)

> An econometric deconstruction of disaster survival on the RMS Titanic (1,305 passengers), isolating confounding variables, physical cabin deck geography, and non-linear sociological interactions.

---

## 💍 Executive Summary

Most analyses treat the Titanic dataset as a trivial classification toy. This project treats it as a historical quasi-experiment in **survival economics, structural privilege, and physical bottleneck constraints**. 

Rather than jumping straight to predictive algorithms, this work performs rigorous **Exploratory Data Analysis (EDA)** to disentangle correlation from causation:
- Deconstructs **confounding variables** (e.g., ticket fare as an economic proxy for physical deck elevation and lifeboat access).
- Unpacks **multi-way interaction terms** between social class, biological sex, and family size.
- Diagnoses **structural missingness** (MNAR vs. MCAR) across cabin allocations and demographic records.

The full methodology, statistical visualizations, and source code are compiled in the 20-page executive report: **[Titanic.pdf](Titanic.pdf)**.

---

## 🔍 Key Empirical Findings

### 1. The Gender _ Class Interaction Matrix
While biological sex is the strongest single predictor (73% overall female survival vs. 19% male), evaluating sex in isolation obscures how socioeconomic rank altered disaster triage:

| Class | Female Survival | Male Survival | Key Structural Mechanism |
|---|:---:<:---:<---|
-| **1st Class** | **96%** (136/141) | **34%** (61/178) | Immediate boat deck access; evacuation protocol prioritization. |
| **2nd Class** | **89%** (94/106) | **15%** (25/171) | Near-total female protection; male sacrifice protocol strictly enforced. |
| **3rd Class** | **49%** (106/216) | **15%** (75/493) | Spatial entrapment in lower decks; physical corridor bottlenecks. |

*Crucial takeaway:* A first-class male was more than twice as likely to survive as a second- or third-class male (34% vs 15%), while third-class women faced a coin-toss probability (49%), despite the "women and children first" protocol.

### 2. Physical Deck Topography vs. Ticket Fare Confounding
Ticket fare correlates strongly with survival ($r = 0.38$), but fare is **not a causal driver**. It is an economic proxy for physical cabin location relative to the boat deck:
- **Upper Deck Cabins (Sectors B, D, E):** Achieved **70% to 73% survival**, situated directly adjacent to central lifeboat davits.
- **Forward Cabins (Sector A):** Dropped to **52%**, physically distant from primary assembly points at the bow.
- **Unrecorded Cabins (`None`, n=1,014):** Survival collapsed to **30%**. This is **Missing Not At Random (MNAR)**--formal cabin assignment records were disproportionately reserved for upper-tier tickets.

### 3. Non-Linear Family Dynamics & Physical Friction
Family size exhibits marked non-linearities rather than monotonic risk:
- **Spouses / Siblings (`sibsp`):** Traveling with exactly one partner increased survival to **51%** (vs. 35% traveling alone), driven by mutual warning and cooperative navigation. Beyond 2 siblings, survival drops sharply to **14%** (4 siblings) and **0%** (5+ siblings), reflecting large third-class emigrant households hindered by evacuation friction.
- **Parents / Children (`parch`):** Follows an inverted U-curve peaking at `parch = 3` (**62% survival**) before collapsing to **17%** for 4–5 and **0%** for 6+.

### 4. Embarkation Port Bias (Simpson's Paradox)
Raw figures suggest Cherbourg passengers survived at **56%** compared to Southampton's **33%**. 
- Controlling for ticket class reveals this is entirely an aggregation artifact: Cherbourg had a **52% first-class composition**, whereas Southampton took on the bulk of third-class labor.

---

## 🛿 Methodological Hygiene & Missing Data Diagnostics

```
Percent Missing Values:
├── body:        91%   (Exclusively recorded for recovered victims)
✜✀✀ cabin:       78%   (Structural MNAR: lower decks unrecorded)
✜── age:         21%   (Imputed using Title/Class median stratifications)
└── fare:       <0.1%  (Single imputation required)
```

- **Target Imbalance:** 28% survived (497) vs. 62% deceased (808). Any naive model predicting uniform mortality hits a baseline accuracy of 62% with zero predictive utility.
- **Feature Engineering Roadmap:** Extracted social honorific titles (`Mr`, `Mrs`, `Miss`, `Master`, `Dr`) as robust proxies for demographic status; constructed `is_alone` indicators; mapped physical cabin deck sectors.

---

## 💻 Tech Stack & Reproduction

- **Environment:** R 4.4+
- **Core Libraries:** `tidyverse` (data wrangling & piping), `ggplot2` (visualization), `patchwork` (multi-chart assemblies), `scales` (formatting)
- **Document Engine:** R Markdown (`.Rmd`) compiled into production vector PDF\n
### Setup & Rendering
```r
# Install dependencies
install.packages(c
  "tidyverse", "patchwork", "scales", "rmarkdown"
))

# Render report to PDF
rmarkdown::render("titanic_eda.Rmd")
```

---

## 📑 References & Primary Sources
- [Encyclopedia Titanica: Demographics & Deck Plans](https://www.encyclopedia-titanica.org/)
- British Wreck Commissioner's Inquiry Report (1912)

---

*jAuthor:** Francesco Colombini  
[GitHub Profile](https://github.com/FRA-0023) § [LinkedIn](https://www.linkedin.com/in/francescocolombini/)

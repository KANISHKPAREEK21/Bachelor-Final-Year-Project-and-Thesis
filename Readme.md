# Bachelor Final Year Project & Thesis

**Predictive Modeling for Earthquakes** — a Bachelor of Technology final year project (AI & Data Science) by **Kanishka Pareek, Aryank Gupta, Muskan Tambi, and Sujal Jain**, Jaipur Engineering College & Research Centre (JECRC), affiliated to Rajasthan Technical University, Kota.

> This repository also includes the team's **Minor Project**, *AID AWARE*, a separate disaster-management mobile app concept developed earlier in the same academic track. Both are documented in this single README.

---

## 📖 Short Description

This project builds and compares seven machine learning regression models (Linear, Ridge, Lasso, Random Forest, Gradient Boosting, SVR, and KNN) to predict earthquake **magnitude** from historical seismic records — latitude, longitude, depth, and region — sourced from India's National Center for Seismology. Gradient Boosting came out on top with the lowest error among the models tested. The repo bundles the full academic trail for this work: the Jupyter notebook, the 52-page thesis report, a standalone research paper, the presentation deck, and the raw seismic datasets used for training.

---

## 📂 Repository Structure

```
Bachelor-Final-Year-Project-and-Thesis/
│
├── Code/
│   └── Earthquake prediction.ipynb          # Main ML notebook (data prep → modeling → evaluation)
│
├── data/
│   ├── Earthquake.csv                       # 14,698 rows — India/Himalayan region seismic events (USGS-style)
│   └── earthquake1.csv                      # 24,007 rows — Turkey/Mediterranean region seismic events
│
├── FINAL YEAR THESIS.pdf                    # 52-page B.Tech final year project report
│
├── Research Paper/
│   └── Research_Paper-_Predictive_Modeling_for_Earthquakes.pdf   # Standalone academic paper version
│
├── Presentation/
│   └── Project PPT Format e-1.pptx          # 19-slide defense/viva presentation
│
└── MINOR Project Synopsis/
    └── Project Synopsis EMERGENCY DISATER Management.pdf         # "AID AWARE" minor project synopsis
```

---

## 🎓 Major Project: Predictive Modeling for Earthquakes

### Overview
Earthquakes are sudden, high-impact natural disasters that conventional warning systems struggle to anticipate. This project frames earthquake forecasting as a **regression problem** — given location and depth information about seismic activity in a region, predict the **magnitude** of an event — and evaluates how well classical and ensemble ML models perform at that task.

### Problem Statement
Existing disaster-prediction systems often rely on simplistic historical analysis and struggle to capture the complex, nonlinear dynamics of seismic activity, real-time data integration, and cross-disciplinary risk factors. This project explores whether supervised ML models trained on government seismic records can meaningfully improve magnitude prediction accuracy and contribute to early-warning and disaster-preparedness pipelines.

### Data
- **Primary source (per thesis):** [National Center for Seismology, Ministry of Earth Sciences, Government of India](https://riseq.seismo.gov.in/riseq/Earthquake/recent_earthquake) — fields include Origin Time, Lat, Long, Depth, Magnitude, Region, and Location.
- **`data/Earthquake.csv`** (14,698 records) — matches this region/style closely: South & Central Asia seismic events (lat ~4°–37°, long ~67°–98°) with magnitude, depth, and USGS-style metadata (`magType`, `gap`, `rms`, `net`, etc.).
- **`data/earthquake1.csv`** (24,007 records) — a separate Turkey/Mediterranean/Greece/Aegean Sea dataset (different schema: `richter`, `mw`, `ms`, `mb`, city/area/direction fields). Appears to be supplementary/reference data, not the dataset directly consumed by the current notebook.
- ⚠️ Note: the notebook itself reads a file literally named `Official Website of National Center of Seismology.csv`, which is **not present** in this repo's `data/` folder — `Earthquake.csv` is the closest match in shape and region and was very likely the intended input (possibly renamed at some point).

### Methodology (as implemented in the notebook)
1. **Data Cleaning** — drop `Origin Time` and `Details` columns; drop rows with missing values.
2. **Encoding** — one-hot encode categorical fields (`Region`, `Location`) via `pd.get_dummies`.
3. **Exploratory Data Analysis** — Seaborn pair plots and a correlation heatmap to inspect relationships between Lat, Long, Depth, and Magnitude.
4. **Feature Selection** — `SelectKBest` with `f_regression` (k=3) to pick the most predictive features. Top features selected: **Depth, Region_Afghanistan, Region_Tajikistan**.
5. **Train/Test Split** — 80/20 split (`random_state=42`).
6. **Model Training** — seven regressors trained and compared on Mean Squared Error (MSE):

   | Model | MSE |
   |---|---|
   | Linear Regression | 0.41 |
   | Ridge Regression | 0.41 |
   | Lasso Regression | 0.45 |
   | Random Forest Regressor | 0.37 |
   | **Gradient Boosting Regressor** | **0.35 (best)** |
   | Support Vector Regressor (SVR) | 0.40 |
   | K-Nearest Neighbors Regressor | 0.40 |

7. **Visualization** — scatter plots of predicted vs. actual magnitude for each model, plus a bar chart ranking all seven models by MSE (best model highlighted).

### Tech Stack
- **Language:** Python 3.9
- **Environment:** Jupyter Notebook
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn` (model_selection, preprocessing, feature_selection, ensemble, linear_model, svm, neighbors, metrics)

### Documents in this Project
| File | What it is |
|---|---|
| `FINAL YEAR THESIS.pdf` | Full academic report — Introduction, Requirement Analysis, Feasibility Study, Technology Used, Project Analysis, UML Diagrams, Testing Methodology, Outputs, Conclusion, Future Scope, References, and Course Outcome mapping. Submitted April 2024. |
| `Research Paper/Research_Paper-_Predictive_Modeling_for_Earthquakes.pdf` | A condensed, standalone research-paper version of the same work (17 pages) authored by all four team members, written for journal/conference-style submission, including related work and a literature-grounded comparison of the seven models. |
| `Presentation/Project PPT Format e-1.pptx` | 19-slide presentation deck: Problem Statement → Objective → Approach → Project Description → Implementation steps (cleaning, visualization, feature selection, training, evaluation) → Tools/Tech → Conclusion → References. |

### Conclusion & Future Scope (from the thesis)
The project concludes that ML-based prediction of earthquake magnitude is feasible and that ensemble methods (Gradient Boosting, Random Forest) outperform simpler linear models on this dataset. Suggested future directions include: deeper multi-source data integration, multi-scale (regional/fault-level) modeling, uncertainty quantification, real-time monitoring and early-warning integration, and closer collaboration with government disaster-management bodies (e.g. NDRF/SDRF).

### How to Run
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook "Code/Earthquake prediction.ipynb"
```
> Note: update the `pd.read_csv(...)` line in the first code cell to point at `../data/Earthquake.csv` (or whichever CSV you intend to use) since the original filename referenced in the notebook isn't included in this repo.

---

## 🚨 Minor Project: AID AWARE — Emergency Disaster Management

A separate, earlier minor project by the same team (submitted August 2024, supervised by Ms. Anima Sharma), proposed as an **Android mobile application** for community-driven disaster response — distinct in scope and tech stack from the earthquake ML thesis above.

### Concept
**AID AWARE** ("Assistance and Information Dissemination – Augmented Response and Emergency") aims to fix the communication and resource-coordination failures common in traditional disaster response systems (floods, earthquakes, etc.) by giving citizens, volunteers, and authorities a single real-time coordination platform.

### Core Features (proposed)
- Push notification & SMS-based disaster alerts
- Personal safety guidance and disaster preparedness tips
- Weather forecasting integration
- Real-time relief-vehicle tracking for safe evacuation
- Volunteer sign-up and mobilization by skill/availability
- Shelter database with live availability/capacity info, and lost-person lookup
- Offline-first design: Bluetooth mesh networking, SMS flow, and IVR (Interactive Voice Response) for zero-connectivity areas
- Twitter/social-media complaint intake routed to disaster authorities (e.g. ASDMA)
- A government-facing control panel with heatmaps and analytics for monitoring crisis situations

### Tech Stack (proposed)
- **Frontend:** Android SDK (Android 4.2 "Lollipop"+)
- **Backend:** Java, PHP (API layer)
- **Database:** SQLite
- **Libraries:** Volley, Glide (and similar Android networking/image libraries)
- **Server requirements:** Windows 8.1+, 4GB+ RAM, 20GB+ storage
- **Client requirements:** Android 4.2+, 512MB+ RAM

### Document in this Project
| File | What it is |
|---|---|
| `MINOR Project Synopsis/Project Synopsis EMERGENCY DISATER Management.pdf` | 10-page project synopsis: Introduction, Objectives, Methodology/Planning, Literature Review, Applications, Block Diagram, UML Diagram, System/Hardware/OS Requirements, References, and team approval page. |

### Relationship to the Major Project
Both projects sit under the same disaster-management theme and were built by the same four-person team, but they are **functionally independent**: AID AWARE (minor) is an application/systems-engineering concept for an Android disaster-response platform, while the earthquake prediction work (major/thesis) is a data science/ML research project focused specifically on forecasting earthquake magnitude from seismic data. The minor project's synopsis predates and is unrelated in implementation to the ML notebook.

---

## 👥 Team

| Name | Roll No. |
|---|---|
| Kanishka Pareek | 20EJCAD029 |
| Aryank Gupta | 20EJCAD012 |
| Muskan Tambi | 20EJCAD046 |
| Sujal Jain | 20EJCAD064 |

**Department:** Artificial Intelligence & Data Science, JECRC, Jaipur
**Affiliation:** Rajasthan Technical University, Kota
**Guide (Major Project):** Ms. Punita Panwar | **HOD:** Dr. Manju Vyas
**Guide (Minor Project):** Ms. Anima Sharma

---

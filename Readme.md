# Bachelor Final Year Project & Thesis

Hi, I'm Kanishka Pareek. This repository holds my Bachelor's final year project — **Predictive Modeling for Earthquakes** — along with the minor project I worked on earlier with the same team. Both were completed as part of my B.Tech in Artificial Intelligence & Data Science at Jaipur Engineering College & Research Centre (JECRC), Jaipur, affiliated to Rajasthan Technical University, Kota.

I worked on this with my teammates **Aryank Gupta, Muskan Tambi, and Sujal Jain**.

---

## About

Earthquakes are one of the most unpredictable and destructive natural disasters — they strike without warning and leave very little time for people to react. That unpredictability is what drew me and my team to this project. We wanted to see how far machine learning could actually take us in forecasting earthquake magnitude using real seismic data, instead of relying purely on traditional statistical methods.

So for our final year project, we built and compared several regression models — Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting, SVR, and KNN — to predict earthquake magnitude based on location and depth data. Gradient Boosting ended up giving us the best results among everything we tried.

This repo brings together everything that came out of that project: the code, the data we trained on, the full thesis report, our research paper, our presentation, and the synopsis of the minor project we did before this one.

---

## Repository Structure

```
Bachelor-Final-Year-Project-and-Thesis/
│
├── Code/
│   └── Earthquake prediction.ipynb          # The main notebook — data prep, models, evaluation
│
├── data/
│   ├── Earthquake.csv                       # Seismic records for the India/Himalayan region
│   └── earthquake1.csv                      # Seismic records for the Turkey/Mediterranean region
│
├── FINAL YEAR THESIS.pdf                    # Our complete final year project report
│
├── Research Paper/
│   └── Research_Paper-_Predictive_Modeling_for_Earthquakes.pdf
│
├── Presentation/
│   └── Project PPT Format e-1.pptx          # Our project defense presentation
│
└── MINOR Project Synopsis/
    └── Project Synopsis EMERGENCY DISATER Management.pdf   # Our minor project, AID AWARE
```

---

## Major Project: Predictive Modeling for Earthquakes

### Why we picked this problem

Existing earthquake prediction systems often lean on historical data and simple statistical models, which struggle to capture how complex and nonlinear seismic activity really is. We wanted to explore whether machine learning could do better — by learning patterns directly from real seismic records rather than relying on rigid assumptions.

### The data

We worked with seismic event data from the **National Center for Seismology, Ministry of Earth Sciences, Government of India**, which records details for each earthquake — when it happened, its latitude and longitude, depth, magnitude, and the region it occurred in. This is the data behind `Earthquake.csv`, covering events across the India and Himalayan belt. We also kept a second dataset, `earthquake1.csv`, covering seismic activity from the Turkey and Mediterranean region, which we used as a reference point while exploring the problem more broadly.

### How we approached it

1. **Cleaning the data** — dropped columns we didn't need, removed rows with missing values, and got the dataset into a usable shape.
2. **Encoding** — converted categorical fields like Region and Location into a numerical format the models could work with.
3. **Exploring the data** — used pair plots and a correlation heatmap to understand how the different variables related to one another.
4. **Feature selection** — used `SelectKBest` to identify the features that mattered most for predicting magnitude. Depth and certain regional indicators came out as the strongest predictors.
5. **Splitting the data** — an 80/20 train-test split.
6. **Training models** — trained and compared seven different regression models:

   | Model | Mean Squared Error |
   |---|---|
   | Linear Regression | 0.41 |
   | Ridge Regression | 0.41 |
   | Lasso Regression | 0.45 |
   | Random Forest Regressor | 0.37 |
   | **Gradient Boosting Regressor** | **0.35 — our best result** |
   | Support Vector Regressor (SVR) | 0.40 |
   | K-Nearest Neighbors Regressor | 0.40 |

7. **Visualizing results** — plotted predicted vs. actual magnitude for each model and compared all seven side by side on a bar chart.

### Tools we used

Python 3.9, Jupyter Notebook, and the usual data science stack — pandas, numpy, matplotlib, seaborn, and scikit-learn.

### The documents in here

- **`FINAL YEAR THESIS.pdf`** — our full project report: introduction, requirement analysis, feasibility study, the technology we used, project analysis, UML diagrams, our testing approach, outputs, conclusion, and future scope. Submitted April 2024.
- **`Research Paper/...pdf`** — we also wrote this up as a standalone research paper, going deeper into related work and comparing our seven models against what's been done in the field.
- **`Presentation/...pptx`** — the slide deck we used to present and defend our project.

### What we concluded

Working through this project showed us that machine learning genuinely can improve earthquake magnitude prediction, and that ensemble methods like Gradient Boosting and Random Forest outperformed the simpler linear models on our data. We see this as a foundation — there's a lot more to explore around real-time monitoring, multi-scale modeling, and working more closely with disaster management authorities to actually put something like this to use.

### Running it yourself

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook "Code/Earthquake prediction.ipynb"
```

---

## Minor Project: AID AWARE — Emergency Disaster Management

Before this final year project, my team and I worked on a minor project called **AID AWARE** — short for *Assistance and Information Dissemination, Augmented Response and Emergency*. It came from a simple frustration: during disasters like floods and earthquakes, communication breaks down and resources don't reach the people who need them fast enough.

We designed AID AWARE as an Android app that would let people share real-time updates, request help, and stay connected during a crisis — built around the idea that technology should make community response faster and more coordinated, not slower.

### What it was meant to do

- Send push notifications and SMS alerts to warn people of incoming disasters
- Give people safety guidance to prepare ahead of time
- Provide weather forecasting to anticipate risk
- Track relief vehicles in real time so people could move to safety
- Let people sign up and coordinate as volunteers
- Maintain a shelter database, including a way to look up missing people
- Work offline using Bluetooth mesh networking, SMS, and IVR, so it wouldn't depend on having an internet connection
- Let people raise issues directly to disaster authorities like ASDMA through social media
- Give the government a control panel to monitor unfolding situations

### Tools we planned to use

Android SDK for the frontend, Java and PHP for the backend, and SQLite for the database — built to run on Android 4.2 and above.

### The document in here

**`MINOR Project Synopsis/...pdf`** — our project synopsis covering the introduction, objectives, our planning approach, a literature review, the block and UML diagrams, and our system requirements.

This was a different kind of project from our final year work — more about building a usable system for people during a crisis, rather than the data science work we did later with earthquake prediction. But both came from the same place: wanting to use what we were learning to actually help people facing disasters.

---

## Team

| Name | Roll No. |
|---|---|
| Kanishka Pareek | 20EJCAD029 |
| Aryank Gupta | 20EJCAD012 |
| Muskan Tambi | 20EJCAD046 |
| Sujal Jain | 20EJCAD064 |

**Department:** Artificial Intelligence & Data Science, JECRC, Jaipur

**University:** Rajasthan Technical University, Kota

**Guide (Major Project):** Ms. Punita Panwar | **HOD:** Dr. Manju Vyas

**Guide (Minor Project):** Ms. Anima Sharma

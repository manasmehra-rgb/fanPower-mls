![image](https://github.com/user-attachments/assets/d7eca846-30e5-4f15-8b8e-0f25f54c1f0a)


# Quantifying the Impact of Attendance on Home Team Performance in Major League Soccer

---

## Overview

This project explores the relationship between **match attendance** and **home team performance** in Major League Soccer (MLS) using publicly available match data. This study isolates attendance as a potential influencing factor on home field outcomes.

The analysis proceeds in three stages:

1. Exploratory analysis of attendance patterns
2. Quantile based comparison of win rates
3. Linear regression to model goal differentials

The findings suggest that while attendance may show a slight association with home success, the effect is minimal and likely overshadowed by other factors.

---

## Research Question

> **Does higher stadium attendance improve home team outcomes in MLS?**

Subquestions include:

* Is there a relationship between crowd size and the likelihood of a home win?
* Does attendance predict the number of goals by which the home team wins or loses?

---

## Dataset

* **matches.csv**: Contains match level data (team names, scores, attendance, dates)
* The dataset was cleaned to remove null scores and remove commas from attendance (initially str type) values
* Only `attendance`, `home_score`, and `away_score` were used (team ratings were excluded to isolate attendance effects)

---

## Methodology

### 1. Attendance Cleaning

* Attendance values were stored as strings with commas and required conversion to integers.
* Matches with missing attendance or scores were excluded.

### 2. Feature Engineering

* `goal_differential` was calculated as `home_score - away_score`
* `home_win` was assigned as 1 if the home team won, else 0

---

## Analysis and Results

### A. Distribution of Attendance

* Match attendance is right-skewed, with a majority of matches attended by 15,000–25,000 spectators.
* A small number of matches exceed 50,000 attendees.

![image](https://github.com/user-attachments/assets/625c7fca-5419-47e5-a198-796133c04864)


### B. Correlation with Win Probability

* The Pearson correlation between `attendance` and `home_win` is approximately **0.0347**, indicating a very weak positive association.

### C. Win Rates by Attendance Bins

* Attendance was divided into 5 quantiles.
* Home win rates slightly increase from the lowest bin (\~47%) to the highest (\~52%), suggesting a mild association between larger crowds and higher win probability.

![image](https://github.com/user-attachments/assets/1775d1f0-9f67-4337-ad82-5ad5cf27e93c)


### D. Linear Regression on Goal Differential

* A linear model was used to predict goal differential from attendance.
* **Slope**: 0.000007
* **Interpretation**: Even a 10,000-person increase in crowd size is associated with only a **0.07 goal** change in outcome.

![image](https://github.com/user-attachments/assets/ee38bee8-3af7-4abb-8411-09d514b13bd3)


---

## Limitations

* The analysis does **not control for confounding variables** such as team quality, opponent strength, or match type. *(Note: I tried to do that but the current data set had to be merged with another data set that had team standings and rankings, but due to a lot of missing values and inconsistent team names in the Data, the merging process was making me go mad!)*
  
* Attendance may correlate with marquee matchups, rivalry games, or high-performing teams, introducing bias.
  
* The relationship captured is associative, not causal.

---

## Conclusion

While higher attendance appears to have a **minor positive association** with home success, the effect is small and not practically significant when isolated from other factors. Future analysis should incorporate team metrics and match context to better understand what drives home-field advantage.

---

## Technologies Used

* Python (Pandas, Seaborn, Matplotlib, Scikit-learn)
* Jupyter Notebook
* CSV data files

---

## Author

**Manas Mehra**
University of Massachusetts Amherst
[mmehra@umass.edu](mailto:mmehra@umass.edu)

---

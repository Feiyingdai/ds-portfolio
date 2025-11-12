# A/B Testing for Player Engagement in *Cookie Cats*


---

## 📚 Table of Contents

- [🌟 Project Overview](#-project-overview)
- [📊 Dataset Overview](#-dataset-overview)
- [🧹 Data Cleaning](#-data-cleaning)
- [📌 Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [📊 Hypothesis Test](#-hypothesis-test)
- [🔍 Bootstrapping](#-bootstrapping)
- [💼 Business Interpretation](#-business-interpretation)

---

## 🌟 Project Overview

### Background
In the mobile gaming industry, sustaining **player engagement** is crucial for long-term success.  
*Cookie Cats*, a popular puzzle game by **Tactile Entertainment**, combines “connect-three” mechanics with a cast of adorable singing cats.  
To balance engagement and monetization, the game introduces **progression gates** — checkpoints where players must either wait or make an in-app purchase to proceed.

---

### Problem Statement
The first gate was originally placed at **level 30**.  
The design team hypothesized that delaying this gate to **level 40** might improve player engagement by providing a smoother early-game experience before encountering any friction point.

This led to an **A/B test** aimed at answering:

>  *Does moving the first progression gate from level 30 to level 40 enhance player engagement during the first week after installation?*

---

### Experiment Design

| Item | Description |
|------|--------------|
| **Control Group (version A)** | Gate at level 30 |
| **Test Group (version B)** | Gate at level 40 |
| **Sample Size** | 90,189 players |
| **Experiment Period** | First 14 days post-installation |
| **Objective** | Measure short-term player engagement |

---

### Metrics Tracked

To evaluate engagement comprehensively, two types of metrics were monitored:

#### Numerical Metrics
| Metric | Description |
|---------|-------------|
| `gamerounds_7d` | Total number of game rounds played within the first 7 days after installation. |

#### Proportion Metrics
| Metric | Description |
|---------|-------------|
| `retention_1_rate` | Proportion of players who returned to play on Day 1 after installation. |
| `retention_7_rate` | Proportion of players who returned to play on Day 7 after installation. |
| `reach_30rounds_rate` | Proportion of players who played **≥ 30 rounds** within the first 7 days. |

---

### Methodology
Findings from this experiment helped the game design team understand how **progression pacing** impacts player engagement.
By quantifying the behavioral impact of gate placement, Cookie Cats could better balance:

🧭 **Engagement** → Keeping players entertained longer

💰 **Monetization** → Maintaining sustainable revenue flow

---

## 📊 Dataset Overview
The dataset contains **90,189 rows**, each representing a unique player who installed the game during the A/B test period.  
Key variables include:

| Column | Description |
|:--------|:-------------|
| `userid` | Unique player identifier |
| `version` | Group assignment: `gate_30`(version A) or `gate_40`(version B) |
| `sum_gamerounds` | Total game rounds played within the first 14 days post-install |
| `retention_1` | Boolean indicating Day-1 retention |
| `retention_7` | Boolean indicating Day-7 retention |

Initial group sizes were well balanced:
- `gate_30`: **44,700 players in control group**  
- `gate_40`: **45,489 players in test group**

---


## 🧹 Data Cleaning

Before proceeding with statistical testing, an initial exploration of the **`gamerounds_7d`** variable revealed a highly skewed distribution with extreme outliers.

### Summary Statistics (Before Outlier Removal)

| version | count | median | mean | std | max |
|:--------|------:|-------:|------:|------:|------:|
| **A** | 44,700 | 17.0 | 52.46 | 256.72 | 49,854 |
| **B** | 45,489 | 16.0 | 51.30 | 103.29 | 2,640 |

> ⚠️ The **maximum value in group A (49,854)** was disproportionately large compared to the median (17), indicating potential outliers that could distort mean-based metrics.

---

### Visual Analysis — Before Removing Outliers

<img width="1284" height="413" alt="image" src="https://github.com/user-attachments/assets/356c1da2-64d5-407d-a5ed-d67a452a7ec1" />


The visualizations show:
- Both **A** and **B** groups have a **long right tail**, with most users playing fewer than 200 rounds within 7 days.
- A few extreme players (particularly in Group A) recorded **tens of thousands of rounds**, likely due to **logging errors or atypical user behavior**.
- These outliers significantly inflated the mean, reducing its representativeness for central tendency.

---

### Data Clean
To ensure robust comparison and avoid distortion, outliers beyond the **maximum of `gamerounds_7d`** were filtered out before conducting hypothesis testing.
<img width="1283" height="410" alt="image" src="https://github.com/user-attachments/assets/0331bea5-d93a-436c-a306-54f46e06450c" />

---

## 📌 Exploratory Data Analysis (EDA)

### Summary Statistics for `gamerounds_7d` 

| Metric | Value |
|:--------|:-------|
| **Count** | 90,188 |
| **Mean** | 51.32 |
| **Std** | 102.68 |
| **Min** | 0 |
| **1%** | 0 |
| **5%** | 1 |
| **10%** | 1 |
| **20%** | 3 |
| **50% (Median)** | 16 |
| **80%** | 67 |
| **90%** | 134 |
| **95%** | 221 |
| **99%** | 493 |
| **Max** | 2,961 |

> The distribution remains right-skewed, with the majority of players completing fewer than 100 rounds during the first 7 days.


### Player Activity Distribution

<img width="636" height="467" alt="image" src="https://github.com/user-attachments/assets/172f580f-9630-40dd-a3e7-f80e3947753c" />

- As players progress through the levels, the number of active users gradually declines.  
- Nearly **5% of users** never play even a single round, and about **63% of users** play **no more than 30 rounds** within the first week.  
- These early drop-offs highlight the importance of **level design and gate placement**, as optimizing progression pacing can help mitigate **player churn** and sustain long-term engagement.


---

### Engagement Depth — Reaching 30+ Rounds

|Version | Player proportion reaching ≥ 30 rounds in 7 days |
|:--------|:-------------|
| A | 37.260% |
| B | 36.521% |

→ Slightly higher Reaching 30+ Rounds player proportion in **Group A**, indicating the earlier gate might help sustain interest.

---
### Retention Analysis — Day 1 and Day 7
<img width="1274" height="465" alt="image" src="https://github.com/user-attachments/assets/394c9ba6-5542-4f57-a602-77147a79bb80" />

- **Day 1 Retention**
  - **Group A (Gate 30):** 20,034 returning users  
  - **Group B (Gate 40):** 20,119 returning users  
  → Engagement levels are almost identical on the first day.

- **Day 7 Retention**
  - **Group A:** 8,501 returning users  
  - **Group B:** 8,279 returning users  
  → Slightly higher retention in **Group A**, indicating the earlier gate might help sustain interest.

---

## 📊 Hypothesis Test

To evaluate whether moving the first progression gate from **level 30** to **level 40** significantly affected player engagement, two categories of metrics were tested using both parametric and non-parametric statistical methods.

---

### Metrics for Hypothesis Testing

Two types of engagement metrics were tracked to capture both **play intensity** and **re-engagement behavior**:

#### Numerical Metric
| Metric | Description |
|:--------|:-------------|
| `gamerounds_7d` | Number of game rounds played within the first 7 days after installation. |

This variable measures **how much time players invest** in the game during their first week.

#### Proportion Metrics
| Metric | Description |
|:--------|:-------------|
| `retention_1_rate` | Proportion of players who returned to play on Day 1 after installation. |
| `retention_7_rate` | Proportion of players who returned to play on Day 7 after installation. |
| `reach_30rounds_rate` | Proportion of players who played **≥ 30 rounds** within the first 7 days. |

These metrics capture the **likelihood of returning** and **depth of engagement**.

---

### Hypothesis Framework

Each metric was tested under the following hypotheses:

- **Null Hypothesis (H₀):**  
  There is **no significant difference** in player engagement between `gate_30` (Group A) and `gate_40` (Group B).

- **Alternative Hypothesis (H₁):**  
  Moving the gate from level 30 to level 40 **significantly changes** player engagement.

---

### Tests Applied

| Metric Type | Statistical Test | Reason |
|--------------|------------------|--------|
| **Numerical** (`gamerounds_7d`) | Mann–Whitney U test |Mann–Whitney is robust to right-skewed data. |
| **Proportion** (`retention_1_rate`, `retention_7_rate`, `reach_30rounds_rate`) | Two-proportion Z-test | To assess whether retention or engagement proportions differ significantly between groups. |

The **Mann–Whitney U test** was chosen for numerical metrics due to the strong right-skew of gameplay distributions, providing a non-parametric alternative to t-tests.

---


### Hypothesis Testing Result

#### Numerical Metric — `gamerounds_7d`

<img width="647" height="380" alt="image" src="https://github.com/user-attachments/assets/0e7c9eda-c7f6-4277-9a4b-8e7f233ea1de" />


| Test Type | Target Variable | Hypothesis Result | p-value | Mean Difference | Effect Size (Cohen’s d) | Comment |
|:-----------|:----------------|:------------------|:--------|:----------------|:-------------------------|:--------|
| Non-Parametric (Mann–Whitney U) | `gamerounds_7d` | Fail to Reject H₀ | **0.0509** | -0.0433 | -0.0004 | No significant difference between A and B |

**Interpretation:**  
- The distributions of gameplay rounds are **heavily right-skewed**, with nearly identical means (A: 51.34 vs B: 51.30).  
- The **Mann–Whitney U test** yielded *p = 0.0509*, slightly above the 0.05 threshold → the difference is **not statistically significant**.  
- Effect size is nearly zero, indicating **no meaningful behavioral change** after moving the gate.

---

#### Proportion Metrics — Retention Rates


| Metric | Test | z-value | p-value | Result | Interpretation |
|:--------|:------|:----------|:----------|:----------|:----------------|
| `retention_1_rate` | Two-Proportion Z-test | 1.787 | **0.0739** | Not Significant | No meaningful difference in Day-1 return rate between A and B. |
| `retention_7_rate` | Two-Proportion Z-test | 3.157 | **0.0016** | **Significant** | Players in Group A (Gate 30) show **higher 7-day retention** compared to Group B (Gate 40). |

**Interpretation:**  
- **Day-1 retention** difference is small and not significant → early re-engagement unaffected by gate position.  
- **Day-7 retention** is **significantly higher for Gate 30**, suggesting that **introducing the first progression gate earlier may encourage longer-term engagement**.

---

#### Proportion Metric — Reaching ≥30 Rounds


| Metric | Test | z-value | p-value | Result | Interpretation |
|:--------|:------|:----------|:----------|:----------|:----------------|
| `reach_30rounds_rate` | Two-Proportion Z-test | 2.301 | **0.0214** | **Significant** | A higher proportion of Group A players reached ≥30 rounds. |

**Interpretation:**  
- The difference in the proportion of players who played ≥30 rounds within the first week is **statistically significant (p < 0.05)**.  
- Group A (Gate 30) had a slightly higher completion rate, indicating that **an earlier progression gate may enhance short-term goal achievement and engagement depth**.

---

### Summary of Hypothesis Testing

| Metric | Type | Test Used | p-value | Significance | Direction |
|:--------|:------|:------------|:----------|:--------------|:------------|
| `gamerounds_7d` | Numerical | Mann–Whitney U | 0.0509 | ❌ Not Significant | — |
| `retention_1_rate` | Proportion | Z-test | 0.0739 | ❌ Not Significant | — |
| `retention_7_rate` | Proportion | Z-test | **0.0016** | ✅ Significant | A > B |
| `reach_30rounds_rate` | Proportion | Z-test | **0.0214** | ✅ Significant | A > B |

> **Conclusion:**  
> While total gameplay rounds (`gamerounds_7d`) remained nearly unchanged, both **7-day retention** and **reach_30rounds_rate** were significantly higher for **Group A (Gate 30)**.  
> This suggests that **introducing the first gate earlier (at Level 30)** encourages deeper and more sustained player engagement within the first week.


---

## 🔍 Bootstrapping

While classical hypothesis testing provides significance levels (p-values), **Bootstrapping** offers a **distribution-free estimate** of metric differences, enhancing robustness and interpretability.

---

### Why Bootstrapping?

Bootstrapping is a **non-parametric resampling technique** that:
- Does **not assume normality** or equal variances, **robust to right-skewed data and outliers**, which are common in gameplay metrics.   
- Provides **empirical confidence intervals (CIs)** for observed differences.
- Enhances the reliability of A/B test inference by replacing theoretical assumptions with empirical evidence, ensuring conclusions remain **robust, interpretable, and reproducible** — especially for skewed or proportion-based engagement metrics.


This makes it especially useful for metrics like `retention_rate` or `gamerounds_7d`, where the distribution deviates from normality.

| Aspect | Traditional Test | Bootstrapping Advantage |
|:--------|:-----------------|:------------------------|
| Distribution Assumption | Normal approximation (Z/t test) | None (empirical sampling) |
| Output | Single p-value | Full distribution + confidence interval |
| Robustness | Sensitive to skew/outliers | Averaged across resamples |
| Interpretability | Significance only | Effect size + uncertainty range |

---

### Bootstrap Implementation

| Parameter | Value |
|:-----------|:--------|
| **Metrics Bootstrapped** | `retention_1_rate`, `retention_7_rate`, `reach_30rounds_rate` |
| **Iterations** | 500 |
| **Sampling Method** | Random sampling *with replacement* from each group |
| **Purpose** | Estimate 95% confidence intervals (CIs) and visualize variability in group differences |

#### Process Summary
1. Randomly resample players the same number of original dataset from Group A and Group B (with replacement).  
2. Compute metric means and their difference per iteration.  
3. Repeat **500 times** to build an empirical distribution of differences.  
4. Derive **95% confidence intervals** from the 2.5th and 97.5th percentiles.  
5. Visualize the bootstrap distributions to inspect overlap and CI coverage of zero.

---

### Bootstrap Results

#### Bootstrapped Δ Distribution — Retention Rates

<img width="1380" height="480" alt="image" src="https://github.com/user-attachments/assets/9ca37e87-45a9-4361-88eb-21552bdd136b" />


| Metric | 95% CI Lower | 95% CI Upper | Significance | Probability (Variant Worse than Control) | Interpretation |
|:--------|:--------------|:--------------|:--------------|:------------------------------------------|:----------------|
| **Retention 1-Day** | -0.012 | +0.001 | ❌ CI Includes 0 | **95.8%** | Although not statistically significant, 95.8% of bootstrap samples show variant (Gate 40) performing **worse** than control (Gate 30). |
| **Retention 7-Day** | -0.013 | -0.004 | ✅ Significant | **99.8%** | Strong evidence that moving the gate to level 40 **reduced 7-day retention**. CI fully below zero. |

**Interpretation:**  
- The 1-day retention difference is not statistically significant since CI includes 0, but the **distribution is skewed negative**, suggesting a consistent downward trend for Gate 40.  
- For 7-day retention, the **entire CI lies below zero**, confirming a significant decline in engagement persistence when the first gate is delayed.

---

#### Bootstrapped Δ Distribution — Reach ≥30 Rounds

<img width="792" height="470" alt="image" src="https://github.com/user-attachments/assets/7fa4f7e8-4a90-4833-a41e-13c78dee4893" />


| Metric | 95% CI Lower | 95% CI Upper | Significance | Probability (Variant Worse than Control) | Interpretation |
|:--------|:--------------|:--------------|:--------------|:------------------------------------------|:----------------|
| **Reach ≥30 Rounds Rate** | -0.013 | -0.001 | ✅ Significant | **99.4%** | The probability that the variant group performed worse than control is 99.4%, confirming that Gate 40 **reduces the likelihood** of players reaching 30 rounds in a week. |

**Interpretation:**  
- Both the CI and probability estimates suggest that players in the **Gate 30** version engage **deeper and more frequently**, achieving 30+ rounds more often than those in Gate 40.  
- This supports the hypothesis that **introducing a progression gate earlier** helps retain user motivation and pacing within the early stages of gameplay.

---

### Summary of Bootstrapping Results

| Metric | Mean Difference (B–A) | 95% CI | Significance | Direction | Comment |
|:--------|:----------------------|:-------------|:--------------|:------------|:-------------|
| `retention_1_rate` | ≈ -0.006 | (-0.012, 0.001) | ❌ Not Significant | A > B | Slight downward trend for Gate 40, not conclusive. |
| `retention_7_rate` | ≈ -0.009 | (-0.013, -0.004) | ✅ Significant | A > B | Clear evidence Gate 40 lowers 7-day retention. |
| `reach_30rounds_rate` | ≈ -0.007 | (-0.013, -0.001) | ✅ Significant | A > B | Gate 40 users less likely to reach 30 rounds. |

> **Conclusion:**  
> Bootstrapped inference strengthens the finding that **the earlier progression gate (Level 30)** yields better engagement outcomes — increasing both **7-day retention** and **play depth** while maintaining comparable early-stage activity.


---

## 💼 Business Interpretation

The combined results from hypothesis testing and bootstrapping reveal consistent and actionable business insights for **Tactile Entertainment’s game design and monetization strategy**.

---

### Interpretation of Player Behavior

- **Earlier gate placement (Level 30)** appears to **motivate players to stay engaged longer** by introducing a sense of progression and mild challenge earlier in the gameplay experience.  
- **Delaying the first gate (Level 40)** may unintentionally **reduce pacing and milestone motivation**, causing some players to disengage before reaching meaningful goals.  
- The gate mechanism acts as a **behavioral checkpoint**, subtly encouraging commitment by providing a break-and-reward cycle — moving it too far may disrupt this rhythm.  

---

### Monetization Implications

- Progression gates not only control pacing but also drive **in-app purchases** (IAP) and **return sessions**.  
- A later gate (Level 40) **reduces friction**, but also lowers retention — fewer players reach the point where purchase decisions typically occur.  
- Maintaining the gate at **Level 30** likely supports better **long-term revenue optimization** by:
  - Keeping more players active in mid-game stages.  
  - Increasing opportunities for engagement-triggered IAP events.  
  - Enhancing repeat-play frequency (as seen in higher 7-day retention).  

---

###  Strategic Recommendations

| Recommendation | Rationale |
|:----------------|:------------|
| **Keep the first progression gate at Level 30** | Optimal balance between engagement pacing and monetization potential. |
| **Experiment with dynamic gate placement** | Personalize gate timing based on player behavior (e.g., fast vs. casual players). |
| **Test additional motivational cues before the gate** | Add small achievements or rewards to maintain flow leading up to the first gate. |
| **Monitor revenue conversion rates in future tests** | Extend the experiment to include IAP and ad monetization metrics for deeper ROI analysis. |

---

> **Business Takeaway:**  
> The earlier progression gate (Level 30) creates a more effective engagement loop — boosting both retention and depth of play — and should remain the default configuration while exploring adaptive, player-level gate tuning in future experiments.


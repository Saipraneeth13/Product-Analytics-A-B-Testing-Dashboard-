# AB Testing Project – Udacity Free Trial Screener

## Overview

This project analyzes an A/B testing experiment conducted by Udacity to evaluate the impact of a new **Free Trial Screener** on student enrollment behavior and long-term retention.

The experiment introduced a prompt asking users how many hours per week they could dedicate to the course before starting the free trial. Students with fewer than 5 hours/week were advised to access the free course materials instead.

The goal was to determine whether this change could:

- Reduce early cancellations
- Improve student experience
- Maintain or improve long-term paid retention

---

## Problem Statement

Udacity observed that many students enrolled in free trials without enough time commitment, resulting in frustration and early cancellation.

To address this, a screening step was added before checkout:

- **5+ hours/week** → continue to checkout normally
- **<5 hours/week** → receive recommendation to access free materials instead

This project evaluates whether the intervention improved meaningful business metrics.

---

## Experiment Screenshot

<img src="Experiment_Screenshot.png" width="700">

---

# Dataset Information

The experiment consists of two groups:

- **Control Group**
- **Experiment Group**

Each dataset contains:

| Column | Description |
|---|---|
| Pageviews | Unique cookies viewing the course page |
| Clicks | Clicks on “Start Free Trial” |
| Enrollments | Students enrolling in free trial |
| Payments | Students remaining after 14 days |

---

# Experiment Design

## Unit of Diversion

- **Cookie-based randomization**

Users were randomly assigned to either:

- Control group
- Experiment group

---

# Metrics Selection

## Invariant Metrics

These metrics should remain statistically similar across both groups.

| Metric | Reason |
|---|---|
| Number of Cookies | Traffic consistency |
| Number of Clicks | Random assignment validation |
| Click Through Probability | Pre-treatment behavior validation |

---

## Evaluation Metrics

| Metric | Formula |
|---|---|
| Gross Conversion | Enrollments / Clicks |
| Retention | Payments / Enrollments |
| Net Conversion | Payments / Clicks |

---

# Hypothesis

## Null Hypothesis (H0)

The screener has no impact on conversion metrics.

## Alternative Hypothesis (H1)

The screener changes user behavior and conversion metrics significantly.

---

# Statistical Parameters

| Parameter | Value |
|---|---|
| Significance Level (α) | 0.05 |
| Statistical Power | 80% |
| Beta (β) | 0.20 |

---

# Sample Size Estimation

## Gross Conversion

<img src="gross_conversion.png" width="700">

Required sample size:

### 25,835 samples per variation

---

## Net Conversion

<img src="net_conversion.png" width="700">

Required sample size:

### 27,413 samples per variation

---

## Retention

<img src="retention.png" width="700">

Required sample size:

### 39,115 samples per variation

---

# Data Visualization

## Number of Cookies

<img src="cookies.png" width="850">

Observation:
- Traffic distribution between groups remained highly consistent.

---

## Number of Clicks

<img src="clicks.png" width="850">

Observation:
- Click behavior was nearly identical across groups.

---

## Click Through Probability

<img src="ctp.png" width="850">

Observation:
- Both groups maintained stable click-through probabilities.

---

# Sanity Check Results

| Metric | Result |
|---|---|
| Cookies | Pass |
| Clicks | Pass |
| Click Through Probability | Pass |

Conclusion:
- Randomization worked correctly.
- No allocation bias was detected.

---

# Evaluation Metric Analysis

## Gross Conversion

<img src="gc.png" width="850">

### Result

- Experiment group showed a significant decrease in gross conversion.
- Fewer students enrolled after seeing the screener.

### Interpretation

The screener successfully filtered students unlikely to commit.

---

## Net Conversion

<img src="nc.png" width="850">

### Result

- Net conversion change was statistically insignificant.

### Interpretation

The reduction in enrollments did not significantly affect the number of paying students.

---

# Weekly Trend Analysis

<img src="week.png" width="850">

### Observations

- Strongest negative impact on Gross Conversion occurred during weekends.
- Net Conversion fluctuations varied by weekday.

This suggests behavioral differences depending on user activity patterns.

---

# Final Results

| Metric | Statistical Significance | Practical Significance |
|---|---|---|
| Gross Conversion | Yes | Yes |
| Net Conversion | No | No |

---

# Conclusion

The experiment successfully reduced free trial enrollments by filtering less-committed users.

However:

- The reduction did not improve net paid conversions significantly.
- The business impact was insufficient to justify a full rollout.

## Recommendation

### Do NOT launch the feature yet.

Instead:

- Conduct additional experiments
- Improve onboarding guidance
- Add prerequisite/course difficulty indicators
- Optimize conversion flow further

---

# Proposed Follow-Up Experiment

## Goal

Reduce early cancellations while improving student retention.

## Proposed Change

Create mentor-led student learning groups after enrollment.

## Hypothesis

Students learning in guided peer groups will:

- Stay engaged longer
- Complete courses more often
- Improve retention rates

## Unit of Diversion

- User-ID

## Evaluation Metric

- Retention Rate

---

# Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- SciPy
- Jupyter Notebook

---

# Key Statistical Techniques

- A/B Testing
- Confidence Intervals
- Z-Test
- Binomial Distribution
- Hypothesis Testing
- Statistical Significance Testing
- Practical Significance Analysis

---

# Project Structure

```bash
AB-Testing-Project/
│
├── ABTestingProject.ipynb
├── README.md
├── Experiment_Screenshot.png
│
├── figure/
│   ├── cookies.png
│   ├── clicks.png
│   ├── ctp.png
│   ├── gc.png
│   ├── nc.png
│   ├── week.png
│   ├── gross_conversion.png
│   ├── net_conversion.png
│   └── retention.png
│
├── data/
│   ├── Final Project Baseline Values.csv
│   ├── Final Project Results - Control.csv
│   └── Final Project Results - Experiment.csv

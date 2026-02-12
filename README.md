# 📈 EE 344 Final Project  
## SPY Next-Day Direction Prediction (1995–2025)

**By Leo Xie and Sibo Zhang**

---

## Application Area

This project focuses on **stock market prediction using machine learning**.  
Specifically, we build a model that predicts whether the **SPY ETF** will go **up or down the next trading day** based on its historical performance.

---

## Dataset Selection

**Source:** MarketWatch  
**Time Range Used:** 1995–2025 (30 years)  

The dataset includes daily:

- Open  
- High  
- Low  
- Close  
- Volume (OHLCV)

We calculate **daily return** from the closing prices for all 30 years.

### Data Split Strategy

- **Training Data:** First 15 years (1995–2009)  
- **Testing Data:** Next 15 years (2010–2025)

This chronological split ensures that the model trains on historical data and is evaluated on future unseen data.

---

## Data Type Characterization

- Structured  
- Unlabeled (binary labels constructed from price movement)  
- Quantitative  
- Time-dependent (time series)

---

## Machine Learning Problem Definition

### Task Type
Binary Classification

We predict whether SPY goes **up or down the next trading day**.

### Input Features (X)

- OHLCV values from the raw dataset  
- Daily return (computed from closing prices)  
- Light feature transformations  

### Target (y)

Binary label:

- `1` → SPY goes up the next day  
- `0` → SPY goes down the next day  

### Success Criteria

A strong outcome means the model:

- Predicts next-day SPY direction **more accurately than random guessing (50%)**
- Consistently outperforms a naive baseline such as **“always predict up.”**

---

## Why Data Science and Machine Learning?

Predicting SPY or financial markets in general is highly challenging because markets are:

- Complex  
- Nonlinear  
- Influenced by investor behavior  
- Affected by macroeconomic conditions, liquidity, and real-world events  

Market behavior is not governed by simple physical laws or deterministic equations.

A data-driven machine learning approach is appropriate because:

- ML models can detect subtle, nonlinear relationships between OHLCV features and next-day returns.
- Models can learn patterns from historical data and attempt to generalize to unseen future data.
- Once trained, the model can automatically generate predictions without manual rule adjustments.
- The same framework can be extended to other stocks, making the approach scalable and robust.

---

## Planned Approaches

### (a) Preprocessing / Feature Work

- Data cleaning  
- Feature construction (daily return)  
- Target construction with time shift (to prevent data leakage)  
- Scaling / normalization (for scale-sensitive models)  
- Time-series split for train/validation/test  

---

### (b) Learning Methods / Models

We will experiment with three models:

1. **Logistic Regression (with L2 regularization)**  
2. **Random Forest**  
3. **Support Vector Machine (SVM)**  

---

## Evaluation Plan

Since this is a classification task, we will report:

- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**
- **ROC-AUC**

### Primary Metric: F1-score

We select **F1-score** as the primary metric because it balances precision and recall.

In financial prediction:
- False positives (predicting “up” incorrectly)
- False negatives (missing true upward movements)

Both types of errors matter, so F1-score provides a balanced evaluation.

### Supporting Metrics

- **Accuracy:** Overall percentage of correct predictions  
- **Precision:** How often predicted “up” days are actually up  
- **Recall:** How many actual “up” days we correctly identify  
- **ROC-AUC:** Measures how well the model separates classes across thresholds  

---

## Train/Test Strategy

We treat the first 15 years as training data and the next 15 years as testing data.

This ensures:

- No look-ahead bias  
- Realistic evaluation on unseen future data  
- Proper time-series modeling practice  

---

## Team Plan

### Sibo
- Download data from 1995–2025  
- Combine into one dataset  
- Compute daily return using Python  

### Leo
- Model training  
- Classification implementation  

### Team
- Evaluate metrics  
- Report results  
- Interpret model performance  

---

## Goal

The goal of this project is to explore whether machine learning models can meaningfully capture patterns in historical SPY data and produce predictive performance better than simple baselines.

Even if prediction accuracy is modest, analyzing model behavior, overfitting, and limitations of financial forecasting is a key part of the project.

---

## Course Information

This final project was completed as part of:

**EE 344: Data-Driven Modeling and Machine Learning**  
Instructor: **Professor Dinuka Sahabandu**

# Day_5

---

# 🚢 Titanic Survival Analysis – README

This project analyzes the Titanic dataset to uncover factors influencing passenger survival. It includes missing data handling, univariate analysis, correlation study, and key survival trends.

---

## 📂 Contents

- [📉 Missing Data Analysis](#-missing-data-analysis)
- [📊 Training Set Statistics](#-training-set-statistics)
- [🔍 Univariate Analysis](#-univariate-analysis)
- [📈 Correlation with Survival](#-correlation-with-survival)
- [🎯 Key Survival Factors](#-key-survival-factors)
- [✅ Conclusion](#-conclusion)

---

## 📉 Missing Data Analysis

| Feature    | Missing Values | % Missing | Action Plan               |
|------------|----------------|-----------|---------------------------|
| `Cabin`    | 687            | 77.1%     | ❌ Drop feature (too sparse) |
| `Age`      | 177            | 19.9%     | 🔧 Impute with median/mean |
| `Embarked` | 2              | 0.2%      | ✨ Fill with mode (`S`)     |

**Decisions:**
- **Drop `Cabin`** due to high sparsity.
- **Impute `Age`** as it's crucial to survival analysis.
- **Fill `Embarked`** with most common value (`S`).

---

## 📊 Training Set Statistics

### 🎯 Survival Rate
- **38.3% survived** (241 out of 629)
- *→ Baseline model must beat 61.7% null accuracy*

### 🛳️ Passenger Class Distribution
| Class | % of Total |
|-------|------------|
| 3rd   | 55.1%      |
| 1st   | 24.2%      |
| 2nd   | 20.7%      |

*→ Majority in 3rd class – important for stratified sampling.*

### 👶 Age Distribution
- **Median**: 28 years  
- **IQR**: 20–38 years  
- **25% under 20**, **25% over 38**  
- *→ Bimodal distribution (children & adults peaks)*

---

## 🔍 Univariate Analysis

### 🎫 Passenger Class (`Pclass`)
- **Survival Rate**:
  - 1st: 63%
  - 2nd: 47%
  - 3rd: 24%
- *→ Strong socioeconomic survival gradient*

### 👩‍👦 Gender (`Sex`)
- **Survival Rate**:
  - Female: 74%
  - Male: 19%
- *→ "Women & children first" policy clearly visible*

### 🧒 Age
- **Right-skewed** distribution
- Majority between 20–40 years
- Few very young or elderly passengers

### 💰 Fare
- **Range**: $0–$512
- 75% paid less than $50
- *→ Highly skewed; reflects socioeconomic divide*

### 🛳️ Embarked Port (`Embarked`)
- Most passengers boarded from:
  - Southampton (S): 72%
  - Cherbourg (C): 19%
  - Queenstown (Q): 9%
- **Survival by Port**:
  - C: 55%
  - Q: 39%
  - S: 34%

---

## 📈 Correlation with Survival

*(Pearson correlation coefficients)*

| Feature     | Correlation | Interpretation |
|-------------|-------------|----------------|
| `Has_Cabin` | +0.32       | Having a cabin ~2× higher survival |
| `Fare`      | +0.26       | Higher fare = higher survival odds |
| `Pclass`    | **-0.34**   | Strongest negative link (3rd class died more) |
| `Age`       | -0.06       | Weakly negative; younger = slightly better survival |
| `SibSp`     | -0.04       | Slightly worse survival with more siblings/spouses |
| `Parch`     | +0.08       | Slight benefit for passengers with parents/children |

---

## 🎯 Key Survival Factors

### 🚹 Gender
- **Female**: 74.20% survival
- **Male**: 18.89% survival

### 🛏️ Passenger Class
- **1st Class**: 62.96%
- **2nd Class**: 47.28%
- **3rd Class**: 24.24%

### 🧳 Cabin Availability
- **Had Cabin**: 66.67%
- **No Cabin**: 29.99%

### ⚓ Embarkation Port
- **Cherbourg (C)**: 55.36%
- **Queenstown (Q)**: 38.96%
- **Southampton (S)**: 33.90%

---

## ✅ Conclusion

### 📌 Most Influential Factors:
1. **Gender** – females had far better odds
2. **Passenger Class** – higher class = higher survival
3. **Cabin Presence** – strong proxy for wealth/class
4. **Fare Paid** – higher fares linked to better survival

### ⚠️ High-Risk Profiles:
- Males
- 3rd class
- No cabin
- Boarded from Southampton

---

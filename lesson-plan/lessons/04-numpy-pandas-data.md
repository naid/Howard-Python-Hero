# Lesson 04 — NumPy, Pandas, and dataset curation

**Time:** 2 weeks (~20 hours)  
**Prerequisite:** [Lesson 03](03-software-engineering.md)  
**Job alignment:** Data engine, large-scale dataset curation

## Learning objectives

- NumPy arrays, broadcasting, vectorization
- Pandas DataFrames for tabular driving data
- Visualization with Matplotlib
- Train/val splits, data quality checks

## 1. NumPy fundamentals

```python
import numpy as np

speeds = np.array([0.0, 13.4, 55.2, 72.1, 10.0])
print(speeds.mean(), speeds.std())
mask = speeds > 50
print(speeds[mask])
```

## 2. Broadcasting

```python
# Normalize each feature column
X = np.random.randn(1000, 4)  # 1000 samples, 4 features
X_norm = (X - X.mean(axis=0)) / X.std(axis=0)
```

## 3. Pandas

```python
import pandas as pd

df = pd.read_csv("driving_log.csv", parse_dates=["timestamp"])
df = df.dropna()
df = df[df["speed"] >= 0]
df["speed_mps"] = df["speed"] * 0.44704
```

## 4. Data quality (curation mindset)

```python
def audit_dataset(df):
    report = {
        "rows": len(df),
        "missing": df.isna().sum().to_dict(),
        "duplicates": df.duplicated().sum(),
        "speed_outliers": (df["speed"] > 150).sum(),
    }
    return report
```

## 5. Splits

```python
from sklearn.model_selection import train_test_split

train, test = train_test_split(df, test_size=0.2, random_state=42)
```

## 6. Visualization

```python
import matplotlib.pyplot as plt

df["speed"].hist(bins=50)
plt.xlabel("Speed (mph)")
plt.savefig("speed_hist.png")
```

## 7. Saving processed datasets

```python
train.to_parquet("train.parquet")
```

Parquet is efficient for large tables — common in production data engines.

## Exercises

1. Load a public dataset (e.g. [UCI Auto MPG](https://archive.ics.uci.edu/ml/datasets/auto+mpg)) — explore with `.describe()`.
2. Build `audit_dataset` for your Lesson 02 CSV.
3. Plot speed vs steering colored by time bucket.

## Mini-project: mini data engine

Pipeline script:

1. Ingest raw CSV
2. Clean (drops, caps outliers)
3. Add derived columns
4. Export train/val parquet + JSON audit report

**Next:** [Lesson 05 — ML foundations](05-ml-foundations.md)

# Lesson 05 — Machine learning foundations

**Time:** 2 weeks (~20 hours)  
**Prerequisite:** [Lesson 04](04-numpy-pandas-data.md)

## Learning objectives

- Supervised learning workflow
- Regression vs classification
- Overfitting, bias-variance
- scikit-learn pipelines and metrics

## 1. The ML workflow

1. Define problem (predict speed category from sensor features)
2. Collect & label data
3. Split train / validation / test
4. Train model
5. Evaluate on **held-out** test set
6. Deploy or iterate

## 2. Simple classifier

```python
from sklearn.linear_model import LogisticRegression
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline

pipe = Pipeline([
    ("scaler", StandardScaler()),
    ("clf", LogisticRegression(max_iter=1000)),
])
pipe.fit(X_train, y_train)
print(pipe.score(X_val, y_val))
```

## 3. Metrics

| Task | Metrics |
|------|---------|
| Classification | accuracy, precision, recall, F1, confusion matrix |
| Regression | MAE, MSE, R² |

```python
from sklearn.metrics import classification_report
print(classification_report(y_val, pipe.predict(X_val)))
```

## 4. Overfitting

- **Train error low, val error high** → overfitting
- Fixes: more data, regularization, simpler model, augmentation

## 5. Cross-validation

```python
from sklearn.model_selection import cross_val_score
scores = cross_val_score(pipe, X, y, cv=5)
print(scores.mean(), scores.std())
```

## 6. Connection to Tesla role

Classical ML is not the end goal — but **data splits, metrics, and baselines** are how teams validate deep learning improvements before shipping.

## Exercises

1. Predict binary label (e.g. high speed vs low) from tabular features.
2. Plot learning curve: model performance vs training set size.
3. Compare LogisticRegression vs RandomForest on same data.

## Mini-project

End-to-end tabular ML repo with `train.py`, `evaluate.py`, saved model `joblib`, and metrics in README.

**Next:** [Lesson 06 — Deep learning theory](06-deep-learning-theory.md)

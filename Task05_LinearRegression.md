# Task 05 — Linear Regression from Scratch

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is Linear Regression?

Linear Regression is a supervised machine learning algorithm that finds the best fitting straight line through a set of data points. The goal is to model the relationship between an input variable and an output variable.

The equation of the line is:

```
y = mx + c
```

where `y` is the predicted value, `x` is the input, `m` is the slope (weight), and `c` is the intercept (bias). The job of the algorithm is to find the best values of `m` and `c` such that the line fits the data as closely as possible.

---

## What is Gradient Descent?

Gradient Descent is the optimization algorithm used to find the best values of `m` and `c`. Instead of solving for them mathematically in one shot, it starts with `m = 0` and `c = 0` and then iteratively nudges them in the direction that reduces the error — like a blindfolded person on a hilly terrain taking small steps downhill until they reach the valley.

Each step is controlled by the **learning rate**. A learning rate that is too large causes the model to overshoot and diverge. A learning rate that is too small means the model takes too long to converge. A value of `0.01` was used here as a safe balance.

The update rules at each iteration are:

```
m = m - learning_rate × gradient_m
c = c - learning_rate × gradient_c
```

This is repeated for 1000 iterations until the weights stabilize.

---

## Dataset

The California Housing dataset from `sklearn.datasets` was used. It contains 20,640 samples with 8 features describing housing blocks in California — including average rooms, population, income, and location. The target variable is the median house price.

For the regression plot, the `AveRooms` feature (average number of rooms) was used as the single input, as plotting requires a 2D graph with one input and one output. The full 8-feature dataset was used for metric evaluation.

---

## Why Normalization is Required

The California Housing features are on very different scales — average rooms ranges from 1 to 10, while population can go up to 35,000. Without normalization, gradient descent behaves erratically because the large-scale features dominate and the "loss surface" becomes distorted.

All features were standardized before training by subtracting the mean and dividing by the standard deviation:

```python
X_norm = (X - X_mean) / X_std
```

This brings every feature to the same scale, centered around 0, which allows gradient descent to converge smoothly.

---

## Implementation

A `LinearRegressionScratch` class was implemented from scratch using only NumPy. No machine learning libraries were used for training.

```python
class LinearRegressionScratch:
    def __init__(self, learning_rate=0.01, iterations=1000):
        self.lr = learning_rate
        self.iterations = iterations
        self.m = 0
        self.c = 0

    def fit(self, X, y):
        n = len(y)
        for _ in range(self.iterations):
            y_pred = self.m * X + self.c
            error = y - y_pred
            dm = (-2 / n) * np.sum(X * error)
            dc = (-2 / n) * np.sum(error)
            self.m -= self.lr * dm
            self.c -= self.lr * dc

    def predict(self, X):
        return self.m * X + self.c
```

The same data was then passed through `sklearn.linear_model.LinearRegression` for comparison.

---

## Results

Both models were evaluated on the same test set using three standard regression metrics.

**MSE (Mean Squared Error)** — average of squared differences between actual and predicted values. Lower is better.

**MAE (Mean Absolute Error)** — average of absolute differences. Less sensitive to outliers than MSE.

**R² Score** — how much of the variance in the data the model explains. Closer to 1.0 is better.

The scratch model and sklearn model produced very similar scores across all three metrics, confirming that gradient descent converged to nearly the same solution as sklearn's exact method.

---

## Comparison

Sklearn's `LinearRegression` uses Ordinary Least Squares (OLS) — a direct mathematical formula that solves for the optimal weights in one step. It is exact by definition.

The scratch model uses gradient descent — an iterative approach that approximates the solution over 1000 steps. Because it is an approximation, it is marginally less precise than OLS. However, the difference in metrics is minimal, which shows that gradient descent with proper normalization and a well-chosen learning rate converges to an answer that is practically equivalent to the exact solution.

The key advantage of understanding gradient descent is that it generalizes to far more complex models — neural networks, deep learning — where OLS cannot be applied. Linear regression from scratch is the foundation for all of that.

---

## Key Takeaways

Normalizing features before gradient descent is essential, not optional. The learning rate controls convergence speed and stability. Sklearn's slight edge in metrics is expected and is a result of using an exact solver rather than an iterative one. Building a model from scratch gives a much deeper understanding of what machine learning libraries are actually doing internally.

---

## Notebook

https://github.com/shahankhugar/UVCE-MARVEL-AI-ML-001/blob/main/LR_updated.ipynb

---
layout: post
title: "Introduction to Linear Regression"
date: 2025-10-10
categories: [Machine Learning]
---
Here we will learn about linear regression which is one of the basic algorithm of supervised machine learning. Machine learning is a subset of artificial intelligence where systems learn and improve from data without explicit programming.

Machine Learning are of three main types-  Supervised Learning, Unsupervised Learning, and Reinforcement Learning

In this post, we’ll explore how it works, what assumptions it makes, and how to implement it in Python.

# Linear Regression
- In basic terms it is - Imagine you have a bunch of dots on a piece of paper. Each dot shows how tall a plant grew depending on how much water it got. Now, you take a ruler and try to draw one straight line that goes as close as possible to all those dots.
That line helps you guess how tall a new plant might grow if you give it a certain amount of water.

 “So, linear regression is just finding the best straight line through some dots, so we can make good guesses!”
- It models the relationship between a dependent variable and one or more independent variables.
Linear regression is one of the most fundamental algorithms in machine learning and statistics.

It helps us understand how one variable (the *dependent variable*) changes when another variable (the *independent variable*) changes.

---

## 🧩 What is Linear Regression?

Linear regression tries to fit a **straight line** through a set of data points in such a way that the **sum of squared errors** (the distances from each point to the line) is minimized.

Mathematically, the line is represented as:

\[
y = β_0 + β_1x + ε
\]

where:
- \( y \) = dependent variable  
- \( x \) = independent variable  
- \( β_0 \) = intercept  
- \( β_1 \) = slope of the line  
- \( ε \) = error term

---

## 📊 Example in Python

```python
import numpy as np
from sklearn.linear_model import LinearRegression

# Sample data
X = np.array([[1], [2], [3], [4], [5]])
y = np.array([2, 4, 5, 4, 5])

# Train model
model = LinearRegression()
model.fit(X, y)

print("Coefficient:", model.coef_)
print("Intercept:", model.intercept_)

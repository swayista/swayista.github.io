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

# What is Linear Regression?

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

Excellent — now we’ll go one level deeper and get the **mathematical intuition** behind linear regression, without jumping straight into formulas.

Let’s build the idea step by step 👇


# Step 1: The Goal

We have some data — points like:

$$
(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n)
$$

For example:

- \(x\): number of study hours  
- \(y\): exam marks  

We believe that **as study hours increase, marks increase in a roughly straight-line way**.

So we want a **line** that best describes this relationship:

$$
\hat{y} = m x + c
$$

where:

- \(m\) is the **slope** (how much \(y\) changes if \(x\) increases by 1)  
- \(c\) is the **intercept** (the predicted \(y\) when \(x = 0\))  


# Step 2: The Idea of “Best Line”

Not all lines will fit the data equally well.  
So we measure **how far off** our line’s predictions are from the actual points.

For each data point:

$$
\text{error}_i = y_i - \hat{y}_i = y_i - (m x_i + c)
$$

We don’t just want the errors to cancel out (some positive, some negative),  
so we square them (to make all positive):

$$
\text{Squared Error}_i = (y_i - (m x_i + c))^2
$$

Then, add them all up:

$$
\text{Total Error} = \sum_{i=1}^{n} (y_i - (m x_i + c))^2
$$


# Step 3: Minimizing the Error

The goal is to find the **values of \(m\)** and **\(c\)** that make this total error as **small as possible**.  

This is called the **method of least squares**.  

So mathematically, linear regression solves:

$$
\min_{m,c} \sum_{i=1}^{n} (y_i - (m x_i + c))^2
$$

That’s an optimization problem — and when you take partial derivatives with respect to \(m\) and \(c\) and set them to zero,  
you get formulas for the best \(m\) and \(c\).



# Step 4: Intuition of Slope and Intercept

- The **slope \(m\)** is how much \(y\) changes *on average* when \(x\) increases by one unit.  
- The **intercept \(c\)** is the average value of \(y\) when \(x = 0\).  

So the line we find is the one that gives the **best average prediction** of \(y\) for a given \(x\).



# Step 5: Broader Intuition

Linear regression is about:

- **Finding patterns** between variables.  
- **Summarizing data** with the simplest possible model (a straight line).  
- **Predicting future outcomes** based on those patterns.



# Example in Python

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
```

---
layout: post
title:  "[ML] Dimensionality Reduction"
date:   2017-12-1
excerpt: "Common dimensionality reduction methods such as PCA and LDA in ML..."
note: true
tag:
- Machine Learning
comments: true
---

Before implementing these dimensionality reduction algorithm, **try to do whatever you want with the raw data first**. In other words, please give yourself a good reason to add more complexity.
{: .notice}


# PCA - Principal Component Analysis

**Problem formulation**:<br> Reduce from **n**-dimension to **k**-dimension: Find \\( k \\) vectors \\( u^{(1)}, u^{(2)}, ..., u^{(k)} \\) onto which to project the data, so as to minimize the **projection error**.
{: .notice}

Usually the data should be ***preprocessed*** by **Feature Scaling / Mean Normalization**.

1. Compute "covariance matrix":

\\[ {\tiny \sum} = \frac{1}{m} \sum_{i = 1}^{n} (x^{(i)}) (x^{(i)})^{T} \\]

2. Compute "eigenvectors" of matrix \\(\tiny \sum \\)

3. Project the raw data onto the k-dimensional space.

**But how to choose \\( k \\)?**

  Typically, choose \\( k \\) to be the smallest value so that:

  \\[ \frac{\frac{1}{m} \sum_{i=1}^{m} \parallel x^{(i)} - x_{approx}^{(i)} \parallel ^2 } {\frac{1}{m} \sum_{i=1}^{m} \parallel x^{(i)} \parallel^2 } \leq 0.01 (0.05) \\]

  In other words, **"99%/95% of the variance is retained."**

**Note:**<br>
**Run PCA just on your training data** and apply the mapping to the cross validation data set and test data set.<br>
{: .notice}

# LDA - Linear Discriminant Analysis
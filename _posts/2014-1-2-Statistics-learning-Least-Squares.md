---
layout: post
title: "Statistics learning----Least Squares"
description: ""
category: 
tags: [Statistics Learning]
---

The linear model has been a mainstay of statistics for the past thirty years. Given the inputs X^T=(X_{1},X_{2},...,X_{p}), we predict Y as output


$$\widehat(Y)=\beta_{0}+\sum_{i=1}^pX_i\beta_i$$


Often it is convenient to include the constant 1 in X to get


$$Y=X^T\beta$$


By using least squares, we pick the coefficients $\beta$ to minimize the RSS(residual sum of squares)


$$RSS(\beta)=\sum_{i=1}^N(y_{i}-x_{i}^T\beta)^2$$
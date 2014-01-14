---
layout: post
title: "Statistics learning least squares"
description: ""
category: 
tags: [Statistics]
---
##Intoduction##

The linear model has been a mainstay of statistics for the past thirty years. Given the inputs `\( X^T=(X_{1},X_{2},...,X_{p}) \)`, we predict Y as output


`\[ \hat{Y}=\beta_{0}+\sum_{i=1}^pX_{i}\beta_{i} \]`


Often it is convenient to include the constant 1 in X to get


`\[ Y=X^T\beta \]`



By using least squares, we pick the coefficients `\( \beta \)` to minimize the RSS(residual sum of squares)


`\[ RSS(\beta)=\sum_{i=1}^N(y_{i}-x_{i}^T\beta)^2 \]`


The solution can be characterized in matrix notation easily, we can write


`\[ RSS(\beta)=(y-X\beta)^T(y-X\beta) \]`


Differentiating with regard to `\( \beta \)` we get


`\[ X^T(y-X\beta)=0 \]`


If `\( X^TX \)` is not singular, the unique solution is given by


`\[ \beta=(X^TX)^{-1}X^Ty \]`


##Coding##
---

---
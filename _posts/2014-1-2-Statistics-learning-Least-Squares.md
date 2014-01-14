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
	x1<-c(0,1,1,3,4,2,4,4,1)
	y1<-c(0,1,2,3,3.2,3,5,3,2)
	plot(x1,y1,pch=16,xlim=c(0,4),ylim=c(0,4))
	k<-solve(t(x1)%*%x1)%*%t(x1)%*%y1
	b<-y1[1]-k*x1[1]
	x=seq(0,4,by=0.02)
	y=k*x+b
	lines(x,y,col="blue",lwd=2)
---
<img src="/assets/2014121.jpg" width="400" height="400"> 

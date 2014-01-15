---
layout: post
title: "Statistics learning perceptron"
description: ""
category: 
tags: [Statistics]
---
##Intoduction##
One of the oldest algorithms used in machine learning (from early 60s) is an online algorithm for learning a linear threshold function called the Perceptron Algorithm.     
Given a training set `\( T=\{(x_{1},y{1}),(x_{2},y_{2}),...,(x_{N},y_{N})\} \)`      
`\( y_{i} \in \{-1,1\},i=1,2,...,N \)`, We want to solve the following issue:     
`\[ min_{w,b}L(w,b)=-\sum_{x_{i} \in M}y_{i}(wx_{i}+b) \]`
`\( M \)` is the set containing the mistaken points.     
Perceptron is a linear classification model, the algorithm goes like this:     
1.Start with the all-zeroes weight vector `\( w=0 \)` , and initialize `\( t \)` to 1. Also let’s automatically scale all examples `\( x \)` to have (Euclidean) length 1, since this doesn’t affectwhich side of the plane they are on.      
2.Given example `\( x \)`,    
3.If `\( y_{i}(wx_{i}+b) \leq 0 \)`     
`\[ w<-w+\eta y_{i}x_{i} \]`
`\[ b<-b+\eta y_{i} \]`
4.goto 2 unless `\( y_{i}(wx_{i}+b) > 0 \)` for all data in the training set.      
##Coding##
---
	x1<-c(3,4,1)     
	x2<-c(3,3,1)     
	ma<-matrix(cbind(x1,x2),ncol=2,nrow=3)     
	y<-c(1,1,-1)     
	omega<-matrix(0:0,nrow=2,ncol=1)     
	b<-0     
	k<-0     
	repeat     
	{     
		for(i in 1:3)     
		{	     
			if((y[i]*(ma[i,]%*%omega+b))<=0)     
			{     
				k<-0     
				omega<-omega+y[i]*ma[i,]     
				b<-b+y[i]     
				break     
			}     
			else k<-1     
		}     
		if(k==1) break     
		i<-1     
	}     
	plot(ma,xlim=c(0,4),ylim=c(0,4),axes=TRUE)     
	x<-seq(0,4,by=0.05)     
	lines(x,y=3-x,col="red",lwd=2)     
---
<img src="/assets/2014141.jpg" width="400" height="400"> 

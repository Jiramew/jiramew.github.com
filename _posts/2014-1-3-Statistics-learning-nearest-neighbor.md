---
layout: post
title: "Statistics learning nearest neighbor"
description: ""
category: 
tags: [Statistics]
---
##Intoduction##
Nearest-Neighbor method utilize the observation in the training set closest in input space to x to form `\( \hat{Y} \)`.Especially, the K-NN(K-Nearest-Neighbor) fit for `\( \hat{Y} \)` is defined as follows     
`\[ \hat{Y}(x)=\frac{1}{k}\sum_{x_{i} \in N_{k}(x)}y_{i} \]`    
where `\( N_{k}(x) \)` is the neighborhood of x defined by the k closest point `\( x_{i} \)` in the training set. We assume Euclidean distance to imply such metric.     

##Coding##
---
	x1<-rnorm(50,0,1)     
	y1<-rnorm(50,0,1)     
	x2<-rnorm(50,2,1)     
	y2<-rnorm(50,2,1     
	x<-cbind(t(x1),t(x2))     
	y<-cbind(t(y1),t(y2))     
	plot(x1,y1,col=2,pch=16,xlim=c(-3,5),ylim=c(-3,5))     
	points(x2,y2,col="blue",pch=16)     
	ch<-function(x,y)     
	{     
		k=0     
		for(i in 1:50)     
		{     
			if(x==x1[i] && y==y1[i])  k=1     
		}     
		return(k)     
	}     
	dis<-function(x1,y1,x2,y2)     
	{     
		distance<-sqrt((x1-x2)^2+(y1-y2)^2)     
		return(distance)     
	}     
	cishu<-16     
	for(tx in seq(-2.5,4,0.05))     
	{     
		for(ty in seq(-2.5,4,0.05))     
		{     
			distan<-c()     
			zdistan<-c()     
			ratio<-0     
			num<-0     
		for(i in 1:100)     
		{     
			distan<-append(distan,dis(x[i],y[i],tx,ty))     
		}     
		for(j in 1:cishu)     
		{     
			zdistan<-append(zdistan,which.max(distan))     
			distan<-distan[-which.max(distan)]     
		}     
		for(c in zdistan)     
		{     
		if(c<51) num<-num+1     
		}     
		ratio<-num/cishu     
		if(ratio==0.5) points(tx,ty,cex=0.7,pch=20)     
		}     
	}	       
---
<img src="/assets/2014131.jpg" width="400" height="400"> 

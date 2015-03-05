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
    library(plotrix)
    x1<-rnorm(50,0,1)
    y1<-rnorm(50,0,1)
    x2<-rnorm(50,2,1)
    y2<-rnorm(50,2,1)
    x<-cbind(t(x1),t(x2))
    y<-cbind(t(y1),t(y2))
    dataSet<-rbind(x,y)
    labels<-append(rep('a',50),rep('b',50))
    
    plot(x1,y1,col=2,pch=16,xlim=c(-3,5),ylim=c(-3,5))
    points(x2,y2,col="blue",pch=16)
    
    distanceCal<-function(x1,y1,x2,y2)
    {
    distance<-sqrt((x1-x2)^2+(y1-y2)^2)
    return(distance)
    }
    
    knnClassify<-function(inX, dataSet, labels, k)
    {
    	points(inX[1],inX[2],col="green",pch=16)
    	labelCatagory = dimnames(as.matrix(table(labels)))[[1]]
    
    	distanceSet = c(0)
    	dataSetSize = length(dataSet[1,])
    
    	for(i in 1:dataSetSize)
    	{
    		distanceSet[i] = distanceCal(inX[1],inX[2],dataSet[,i][1],dataSet[,i][2])
    	}
    	distanceSetOrigin = distanceSet
    	
    	nnIndex = c(0)
    	for(j in 1:k)
    	{
    		nnIndex[j] = which.min(distanceSet)
    		distanceSet[nnIndex[j]] = max(distanceSet)+1
    	}
    
    	draw.circle(inX[1], inX[2], max(distanceSetOrigin[nnIndex]), nv=10000,border="green")
    	
    	countLabel<-c(0,0)
    	for(l in 1:k)
    	{
    		if(labels[nnIndex[l]] == labelCatagory[1]) countLabel[1]=countLabel[1]+1
    		else countLabel[2]=countLabel[2]+1
    	}
    
    	if(countLabel[1]>countLabel[2]) return(labelCatagory[1])
    	else return(labelCatagory[2])
    }
    
    knnClassify(c(0,0),dataSet,labels,5)
    
---
<img src="/assets/2014131.png" width="400" height="400"> 

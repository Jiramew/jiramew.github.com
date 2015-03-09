---
layout: post
title: "Statistics learning K-means and DBSCAN"
description: ""
category: 
tags: [Statistics]
---
##K-means##

###Coding###
---
	set.seed(12345)

	x1 <- rnorm(50, 0, 1)
	y1 <- rnorm(50, 0, 1)
	x2 <- rnorm(50, 3, 1)
	y2 <- rnorm(50, 3, 1)
	x <- cbind(t(x1), t(x2))
	y <- cbind(t(y1), t(y2))
	dataSet <- rbind(x, y)
	label <- append(rep(1, 50), rep(2, 50))

	par(mfrow = c(1, 2))

	plot(x1, y1, col = 2, pch = 16, xlim = c(-3, 6), ylim = c(-3, 6))
	points(x2, y2, col = "blue", pch = 16)

	ranLabel <- sample(c(1, 2), 100, r = T)

	ranx1 <- dataSet[1, which(ranLabel == 1)]
	rany1 <- dataSet[2, which(ranLabel == 1)]

	ranx2 <- dataSet[1, which(ranLabel == 2)]
	rany2 <- dataSet[2, which(ranLabel == 2)]

	points(ranx1, rany1, col = "red", pch = 16)
	points(ranx2, rany2, col = "blue", pch = 16)

	x01 <- mean(dataSet[1, which(ranLabel == 1)])
	y01 <- mean(dataSet[2, which(ranLabel == 1)])

	x02 <- mean(dataSet[1, which(ranLabel == 2)])
	y02 <- mean(dataSet[2, which(ranLabel == 2)])

	points(x01, y01, col = "green", pch = 16)
	points(x02, y02, col = "green", pch = 16)

	dist <- function(x1, y1, x2, y2) {
		distance <- sqrt((x1 - x2)^2 + (y1 - y2)^2)
		return(distance)
	}

	sumdist <- function(label) {
		sum = 0
		for (i in 1:100) {
			if (label[i] == 1) 
				sum = sum + dist(dataSet[1, i], dataSet[2, i], x01, y01) else sum = sum + dist(dataSet[1, i], dataSet[2, i], x02, y02)
		}
		return(sum)
	}

	plot(x1, y1, col = 1, pch = 16, xlim = c(-3, 6), ylim = c(-3, 6))
	points(x2, y2, col = 1, pch = 16)

	k = 0

	newLabel = ranLabel

	repeat {
		
		j = sumdist(newLabel)
		
		for (i in 1:100) {
			if (dist(dataSet[1, i], dataSet[2, i], x01, y01) <= dist(dataSet[1, i], 
				dataSet[2, i], x02, y02)) 
				newLabel[i] = 1 else newLabel[i] = 2
		}
		
		x01 <- mean(dataSet[1, which(newLabel == 1)])
		y01 <- mean(dataSet[2, which(newLabel == 1)])
		x02 <- mean(dataSet[1, which(newLabel == 2)])
		y02 <- mean(dataSet[2, which(newLabel == 2)])
		
		inloopx1 <- dataSet[1, which(newLabel == 1)]
		inloopy1 <- dataSet[2, which(newLabel == 1)]
		
		inloopx2 <- dataSet[1, which(newLabel == 2)]
		inloopy2 <- dataSet[2, which(newLabel == 2)]
		
		points(inloopx1, inloopy1, col = "red", pch = 16)
		points(inloopx2, inloopy2, col = "blue", pch = 16)
		
		points(x01, y01, col = "green", pch = 16)
		points(x02, y02, col = "green", pch = 16)
		k = k + 1
		delta = j - sumdist(newLabel)
		if (delta < 1 | k > 10) 
			break
	} 
---
<img src="/assets/kmeans.png" width="800" height="400"> 
---
##DBSCAN##

###Coding###
---
	library(plotrix)

	set.seed(12345)

	x1 <- rnorm(50, 0, 0.6)
	y1 <- rnorm(50, 0, 0.6)
	x2 <- rnorm(50, 4, 0.6)
	y2 <- rnorm(50, 4, 0.6)
	x <- cbind(t(x1), t(x2))
	y <- cbind(t(y1), t(y2))
	dataSet <- rbind(x, y)
	label <- append(rep(1, 50), rep(2, 50))

	par(mfrow = c(1, 2))

	plot(x1, y1, col = 2, pch = 16, xlim = c(-3, 6), ylim = c(-3, 6))
	points(x2, y2, col = "blue", pch = 16)

	r <- 0.7
	MinPts <- 5
	c = 0 
	newLabel <- rep(c, 100)

	dist <- function(x1, y1, x2, y2) {
		distance <- sqrt((x1 - x2)^2 + (y1 - y2)^2)
		return(distance)
	}

	getneigh <- function(x0, y0, r) {
		dataX <- dataSet[1, ] - x0
		dataY <- dataSet[2, ] - y0
		distance <- sqrt(dataX^2 + dataY^2)
		inpoint <- which(distance < r)
		draw.circle(x0, y0, r, nv = 10000, border = "green")
		return(inpoint)
	}

	for (i in which(newLabel == 0)) {
		if (newLabel[i] == 0) {
			seed <<- c()
			eps = getneigh(dataSet[1, i], dataSet[2, i], r)
			N = length(eps)
			if (N < MinPts) {
				newLabel[i] <- -1
				next
			} else {
				c = c + 1
				newLabel[eps] <- c
				seed <- c(seed, eps)
			}
			repeat {
				for (j in seed) {
					cureps = getneigh(dataSet[1, j], dataSet[2, j], r)
					curN = length(cureps)
					if (curN >= MinPts) {
					  for (k in cureps) {
						if (newLabel[k] == 0) {
						  newLabel[k] <- c
						  seed <- c(seed, k)
						}
					  }
					}
					seed <- seed[-which(seed == j)]
					if (length(seed) == 0) 
					  break else next
				}
				if (length(seed) == 0) 
					break
			}
			next
		}
	}

	plot(x1, y1, col = 1, pch = 16, xlim = c(-3, 6), ylim = c(-3, 6))
	points(x2, y2, col = 1, pch = 16)

	drawlabel <- function(dataSet, label) {
		k <- 1
		n <- as.numeric(rownames(as.matrix(table(label))))
		for (i in n) {
			x <- dataSet[1, which(label == i)]
			y <- dataSet[2, which(label == i)]
			points(x, y, col = k, pch = 16)
			k <- k + 1
		}
	}
	drawlabel(dataSet, newLabel) 

---
<img src="/assets/DBSCAN.png" width="800" height="400"> 
---
##COMPARE##

###Coding###
---
    x1<-seq(from=0,to=4,length=50)
    y1<-seq(from=2,to=4,length=50)
    x2<-seq(from=-2,to=2,length=50)
    y2<-seq(from=0,to=2,length=50)
    x<-cbind(t(x1),t(x2))
    y<-cbind(t(y1),t(y2))
    dataSet<-rbind(x,y)
    label<-append(rep(1,50),rep(2,50))
---
<img src="/assets/comkmeans.png" width="800" height="400"> 
<img src="/assets/comDBSCAN.png" width="800" height="400"> 
---
layout: post
title: "Stochastic Process ARIMA"
description: ""
category: 
tags: [Stochastic]
---
##Intoduction##

##Coding##
---
1.Load the Package:      
	library('forecast')            
	library(tseries)      
	data<-AirPassengers      
2.Plot for intuitive judgment      
	ts.plot(data)      
	acf(data)      
	pacf(data)      
	decom<-decompose(data)      
	plot(decom)      
3.Do the forecast      
    airts<-ts(data,start=1949,frequency=12)      
    arima1<-auto.arima(airts,trace=T)      
	tsdiag(arima1)      
	datafore<-forecast(arima1,h=30,fan=T)   
	plot(datafore)
---
<img src="/assets/2014161.jpg" width="400" height="400"> 
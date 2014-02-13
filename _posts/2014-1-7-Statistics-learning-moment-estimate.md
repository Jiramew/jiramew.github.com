---
layout: post
title: "Statistics Learning Moment Estimate and MLE"
description: ""
category: 
tags: [Statistics]
---
#Moment Estimation#
##Intoduction##
For random variables, the moment is most widely used numerical characteristics. It was first presented by Pearson in 1894. By moment estimate we can estimate the unknown parameters by samples instead of the population.            
Everything we need to know is to remember the ME(moment estimate) of each distribution by using the basic knowledge in Statistics.       
##Example1(Normal Disrtibution)##
	x=rnorm(1000,1,2)     
	mean=mean(x)     
	stde=sd(x)     
##Example2(Binomial Distribution)##    
First we can see that the two parameters satisfy the following expression( for B(n,p) )：       
`\[\begin{equation}
   \left\{
   \begin{aligned}
	np=M_{1}\\
	np(1-p)=M_{2}\\
   \end{aligned}
   \right.
   \end{equation}\]`      
we need the funciton to compute the moment.       

	moment <-function(para)      
	{        
	fun<-c(para[1]*para[2]-M1,para[1]*para[2]-para[1]*para[2]^2-M2)      
	Jacobi<-matrix(c(para[2],para[1],para[2]-para[2]^2,para[1]-2*para[1]*para[2]),nrow=2,byrow=T)      
	list(fun=fun,Jacobi=Jacobi)      
	}
	
And the Newton method to solve the equation.   
  
	Newton<-function (fun, x, ep=1e-5,it_max=100)        
	{        
	index<-0; k<-1        
	while (k<=it_max){        
	x1 <- x; obj <- fun(x);        
	x <- x - solve(obj$J, obj$f);        
	norm <- sqrt((x-x1) %*% (x-x1))        
	if (norm<ep){        
	index<-1; break        
	}        
	k<-k+1        
	}        
	obj <- fun(x);        
	list(root=x, it=k, index=index, FunVal= obj$f)        
	}
	
Now we can test this method       
    
	x<-rbinom(1000, 10, 0.5); n<-length(x)       
	M1<-mean(x);M2<-(n-1)/n*var(x)       
	para_0<-c(5 , 0.2)       
	Newtons(moment , para_0)       
	
#MLE#
For One-Parameter Distribution, we usually use the logarithm likehood function.       
We can use the function "optimize()" to compute the MLE of a specific distribution.       
##Example(Poisson Distribution)##
For `\( P(\lambda) \)` the logarithm likehood function for `\( X_{1},X_{2}...X_{n} \)` is
`\[ l_{\lambda}(X)=\frac{\lambda^{\sum_{i=1}^{n}x_{i}}e^{10\lambda}}{\Gamma(x_{1}+1)\Gamma(x_{2}+1)...\Gamma(x_{n}+1)} \]`
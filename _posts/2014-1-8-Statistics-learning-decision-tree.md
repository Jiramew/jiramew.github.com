---
layout: post
title: "Statistics Learning Decision Tree"
description: ""
category: 
tags: [Statistics]
---
#Decision Tree#
##Intoduction##
Classification Decision Tree model is a tree structure for classifing the sample data. Decision Tree consists of nodes and directed edges. Also, there are two types of node, internal node and leaf node.

By using the decision tree, from the root node, we test some characteristics. According to the result, we allocate the sample to the son node. So every son node denotes the value of the corresponding  characteristic. Therefore, we can test and allocate the sample recursively until we arrive at the leaf node.

The picture below is a sketch map of decision tree. The circles are internal nodes and the squares denotes leaf nodes.

<center>
<img src="/assets/decisiontree.jpg" width="300" height="240" align="center">
</center>

Obviously, we could regard the decision tree as a set of if-then principle. Every route connecting the root node and leaf node has a term with if-then structure. Moreover, this structure is complete and muturally-exclisive, which means each sample is covered by one and only route or principle.

##Decision Tree Lerning##
Giving the training set 

`\[ D={(x_{1},y_{1}),(x_{2},y_{2}),...,(x_{N},y_{N})\]`

and, `\( x_{i}=(x_{i}^{(1)},x_{i}^{(2)},...,x_{i}^{(n)})^{T}\)`  
   
##Example2(Binomial Distribution)##
First we can see that the two parameters satisfy the following expression( for B(n,p) )：       

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
`\[ l_{\lambda}(X)=log(\frac{\lambda^{\sum_{i=1}^{n}x_{i}}e^{-n\lambda}}{\Gamma(x_{1}+1)\Gamma(x_{2}+1)...\Gamma(x_{n}+1)})=-n\lambda+(\sum_{i=1}^{n}x_{i})log(\lambda)-\sum_{i=1}^{n}log(\Gamma(x_{i}+1)) \]`

	n<-100       
	x<-rpois(n,5)       
	sum<-sum(x)       
	Prodgamma<-function(x)       
	{       
		prod=1       
		for(i in 1:length(x))       
		{       
			prod=prod*gamma(x[i]+1)       
		}       
		return(prod)       
	}       
	f<-function(lambda)       
	{       
		-n*lambda+sum*log(lambda)-log(Prodgamma(x))       
	}       
	optimize(f,c(3,7),maximum=T)       
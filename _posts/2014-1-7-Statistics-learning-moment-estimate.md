---
layout: post
title: "Statistics Learning Moment Estimate"
description: ""
category: 
tags: [Statistics]
---
##Moment Estimation##
#Intoduction#
For random variables, the moment is most widely used numerical characteristics. It was first presented by Pearson in 1894. By moment estimate we can estimate the unknown parameters by samples instead of the population.            
Everything we need to know is to remember the ME(moment estimate) of each distribution by using the basic knowledge in Statistics.       
#Example1(Normal Disrtibution)#
	x=rnorm(1000,1,2)     
	mean=mean(x)     
	stde=sd(x)     
#Example2(Binomial Distribution)
	x=rbinom(1000,5,0.5)      
we need the funciton to compute the moment. First we can see that the two parameters satisfy the following expression(for B(n,p))：       
`\[\begin{equation}
   \left\{
   \begin{aligned}
	np=M_{1}\\
	np(1-p)=M_{2}\\
   \end{aligned}
   \right.
   \end{equation}\]` 
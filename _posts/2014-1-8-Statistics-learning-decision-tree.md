---
layout: post
title: "Statistics Learning Decision Tree"
description: ""
category: 
tags: [Statistics]
---
##Intoduction##
Classification Decision Tree model is a tree structure for classifing the sample data. Decision Tree consists of nodes and directed edges. Also, there are two types of node, internal node and leaf node.

By using the decision tree, from the root node, we test some characteristics. According to the result, we allocate the sample to the son node. So every son node denotes the value of the corresponding characteristic. Therefore, we can test and allocate the sample recursively until we arrive at the leaf node.

The picture below is a sketch map of decision tree. The circles are internal nodes and the squares denotes leaf nodes.

<center>
<img src="/assets/decisiontree.jpg" width="400" height="360" align="center">
</center>

Obviously, we could regard the decision tree as a set of if-then principle. Every route connecting the root node and leaf node has a term with if-then structure. Moreover, this structure is complete and muturally-exclisive, which means each sample is covered by one and only route or principle.

##Decision Tree Lerning##
Giving the training set 

`\[ D=\{(x_{1},y_{1}),(x_{2},y_{2}),...,(x_{N},y_{N})\}\]`

and, `\( x_{i}=(x_{i}^{(1)},x_{i}^{(2)},...,x_{i}^{(n)})^{T}\)`  is the input sample set, `\( y_{i} \in \{1,2,...,K\} \)`is the symbol of the class `\( i=1,2,...,N \)`, N is the sample capacity. The purpose of learning is to construct a decision tree model according to the given training set, which could classify the sample correctly.
   
##How to select the characteristic##
###Example(Loan or Not)###
<center>
<img src="/assets/decisiontree2.jpg" width="500" height="300" align="center">
</center>



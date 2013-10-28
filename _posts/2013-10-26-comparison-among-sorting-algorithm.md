---
layout: post
title: "Comparison Among Sorting Algorithm"
description: ""
category: 
tags: []
---

comparison among different sorting algorithm.
---
##Bubble Sort##
	void BubSort(int array[],int n)
	{
		for(int i=0;i<n-1;i++)
		{
			for(int j=i+1;j<n;j++)
			{
				if(array[i]>array[j])
				{
					int tem=array[i];
					array[i]=array[j];
					array[j]=tem;
				}
			}
		}    
	}
---
##Select Sort##
	void SelectSort(int array[],int n)
	{
		int min;
		for(int i=0;i<n-1;i++)
		{
			min=i;
			for(int j=i+1;j<n;j++)
			{
				if(array[j]<array[min]) min=j;
			}
			if(min!=i)
			{
				int tem=array[i];
				array[i]=array[min];
				array[min]=tem;
			}
		}
	}
---
##Insert Sort##
	void InsertSort(int array[],int n)
	{
		for(int i=1;i<n;i++)
		{
			int tem=array[i];
			int j=i-1;
			while(j>=0&&array[j]>tem)
			{
				array[j+1]=array[j];
				j--;
			}
			array[j+1]=tem;
		}
	}
---
##Shell Sort##
	void ShellSort(int array[],int n)
	{
		for(int in=n/2;in>0;in/=2)
		{
			for(int k=0;k<(n-1)/in;k++)
			{
				for(int i=k+in;i<n;i+=in)
				{
					int tem=array[i];
					int j=i-in;
					while(j>=0&&array[j]>tem)
					{
						array[j+in]=array[j];
						j-=in;
					}
					array[j+in]=tem;
				}
			}
		}
	}
---
##Quick Sort##
	void swap(int &a,int &b){int t;t =a ;a =b ;b =t ;} 
	int Partition(int array[],int low,int high) 
	{ 
		int p=array[low];
		while (low < high) 
		{ 
			while (low < high && array[high] >= p) 
			{ 
				--high; 
			} 
			swap(array[low], array[high]); 
			while (low <high &&array [low ]<=p ) 
			{ 
				++low ; 
			} 
			swap (array [low ],array [high ]);
		}       
		return low ;
	} 
	void QuickSort(int a[],int low,int high,int num)
	{     
		if (low <high ) 
		{ 
			int n=Partition (a ,low ,high ); 
			QuickSort (a ,low ,n ,num); 
			QuickSort (a ,n +1,high ,num); 
		}       
	} 
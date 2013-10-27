---
layout: post
title: "Comparison Among Sorting Algorithm"
description: ""
category: 
tags: []
---
{% include JB/setup %}

comparison among different sorting algorithm.
---
##Bubble Sort##
	void BubbleSort(int arr[],int n)
	{
		for(int i=0;i<n-1;i++)
		{
			for(int j=i+1;j<n;j++)
			{
				if(arr[i]>arr[j])
				{
					int temp=arr[i];
					arr[i]=arr[j];
					arr[j]=temp;
				}
			}
		}    
	}
---
##Selection Sort##
	void SelectSort(int arr[],int n)
	{
		int min_index;
		for(int i=0;i<n-1;i++)
		{
			min_index=i;
			for(int j=i+1;j<n;j++)
			{
				if(arr[j]<arr[min_index])min_index=j;
			}
			if(min_index!=i)
			{
				int temp=arr[i];
				arr[i]=arr[min_index];
				arr[min_index]=temp;
			}
		}
	}
---
##Insert Sort##
	void InsertSort(int arr[],int n)
	{
		for(int i=1;i<n;i++)
		{
			int temp=arr[i];
			int j=i-1;
			while(j>=0&&arr[j]>temp)
			{
				arr[j+1]=arr[j];
				j--;
			}
			arr[j+1]=temp;
		}
	}
---
##Shell Sort##
	void ShellSort(int arr[],int n)
	{
		for(int incr=n/2;incr>0;incr/=2)
		{
			for(int L=0;L<(n-1)/incr;L++)
			{
				for(int i=L+incr;i<n;i+=incr)
				{
					int temp=arr[i];
					int j=i-incr;
					while(j>=0&&arr[j]>temp)
					{
						arr[j+incr]=arr[j];
						j-=incr;
					}
					arr[j+incr]=temp;
				}
			}
		}
	}
---
##Quick Sort##
	void swap(int &a,int &b){int t;t =a ;a =b ;b =t ;} 
	int Partition(int arr[],int low,int high) 
	{ 
		int pivot=arr[low];
		while (low < high) 
		{ 
			while (low < high && arr[high] >= pivot) 
			{ 
				--high; 
			} 
			swap(arr[low], arr[high]); 
			while (low <high &&arr [low ]<=pivot ) 
			{ 
				++low ; 
			} 
			swap (arr [low ],arr [high ]);
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
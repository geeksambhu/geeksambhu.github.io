---
title: QuickSort Algorithm in Python
layout: post
tags:
  - Quicksort Algorithm,  python,  Algorithm
category:
  - Algorithm
description: Quicksort Algorithm in Python
---

## Introduction to Quick Sort Algorithm

A sorting algorithm basically sorts the data structure like array or list in certain order. The order either may be the numerical order or alphabetical order.

A `Quick-Sort` Algorithm is one of the fastest sorting algorithms, which sorts the array based on partitioning by choosing an element of the same array as a pivot. All element greater than the pivot are moved to the right direction and all element smaller than the pivot are moved to left.

The basic idea of this algorithm is to select a pivot element in an array and to put the pivot element in its right place and move all smaller entries than pivot of the array to left, and greater entries than pivot to right of the array.
Now the array is divided into two part one part of greater entries than the current pivot element and another part of the smaller entries than the current pivot element.
Now the two-part are recursively applied quicksort to left part and to the right part. Recursion basically refers to a function having its own application within its definition.

## Things to consider while applying Quick Sort

### Pivot element should be chosen carefully

The pivot element is responsible for the efficiency of this algorithm, depending upon pivot element the sorting operation could be really fast or slow.

Common practices for choosing pivot element are:

- Choosing the fixed element of the given array. the fixed element may be the array of index 0 or index n-1, i.e the first and last or middle.

  - Choosing the fixed element of the given array. the fixed element may be the array of index 0 or index n-1, i.e the first and last or middle.

- Choosing randomly by random generator.
- Choosing by taking the median element as pivot, i.e (N/2) element if the array is of size N.and it results in computational complexity.
- Taking the first, middle and the last element and choosing the medium element from the selection for Pivot element.

## Complexity of QuickSort Algorithm

In Worst case, time complexity will be O(N<sup>2</sup>) , i.e, it occurs when the pivot element, chosen was smallest or largest resulting one partition to be empty,
In the best case, time complexity will be O(NlogN), where N is the number of items and this occurs when the pivot is the median of the array which results in the equal partition on left and right.

## Python Implementation

{% highlight python %}
def quick_sort(given_list):
if len(given_list) < 1:
return given_list
else:
pivot_element = given_list[0]
#here I am choosing the first element to be a pivot
  
 left = quick_sort([element for element in given_list[1:] if element < pivot_element])
#moving smaller to left
  
 right = quick_sort([element for element in given_list[1:] if element > pivot_element])
#moving greater to right
return left + [pivot_element] + right
#usage
mylist=[8,5,9,4,3,7,2,12,10]
print (quick_sort(mylist))
#Outputs [2, 3, 4, 5, 7, 8, 9, 10, 12]
{% endhighlight %}

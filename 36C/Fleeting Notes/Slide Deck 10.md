Created: 2022-03-05 16:24
Status: #idea
Tags: [[Data Structures]]
# Slide Deck 10
## Temporay Assumptions
* All keys are integers
* All keys are unique

## Selection Sort
What is selection Sort?
It views a list as two partitions
1. A sorted part
	1. Initially Empty
2. Unsorted Parts
* Until Part 2 is empty we add the smallest element to part 1.
The Worst Time Complexity for this sort would be $\theta$($n^2$)

## Insertion Sort
Views list as two parts
1. Sorted Part.
	1. Usually first element
2. Unsorted Part

The Worst Time Complexity for this would be $\theta$($n^2$)
* Nested Loops 

## Mergesort
Divide and conquer algorithm
Steps:
1. Divide unsorted list into two equal halves			
2. Conquer: recursively mergesort each half.
	* The view the Base Case as 
		1. one or two elements remain
		2. one element remain
3. Combine two sorted halves into final sorted list

```ad-note
![[Screenshots/Pasted image 20220305174829.png]]
```

## Quicksort 
A divide and conquer algoirthm 
Uses the first choice pviot rule
Steps:
1. Chooses pivot element $v$ in list. *Divide* list into two halves. Makes first half have less elements than $v$ and second half has elements greater than $v$
	1. $v$ is excluded from both halves. After this partitioning, we know $v$ is in final spot.
2. *Conquer*: recursively quicksort from each half. 
	* Base case: 0 and 1 elements remain

3. Combine two sorted halves into final sorted list.
	* This phase is trivial compared to mergesorts.

### Picking Pivots
* Bad Ways:
	* Choose first element
	* Choose large or first two distinct elements
* Choose random pivot
* The Best: Median-of-three partioning -> choose median of first, center, and last element




# References
1. https://canvas.ucdavis.edu/courses/632689/files/folder/ECS%2036C%20Lecture%20Slides?preview=16114948

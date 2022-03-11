Created: 2022-03-07 21:10
Status: #idea
Tags:
# Quicksort
- Divide and conquer algorithm
- Picks element as pivot and paritions the given array around the picked pivot
- Are many versions that pick pivot in different ways.
1. always pick first element as pivot(first choice pivot)
2. always pick last element as pivot
3. pick a random element as pivot

- Considered as an *in-place sorting algorithm*.

#### Time Complexity
O(nlogn) - Average case running time
O(n$^2$) - Worst case running time
in-Place 

```ad-example
Lets say we want to sort the array into increasing order 
![[Screenshots/Pasted image 20220307211828.png]]
```

We select any element from the list and so we can pick number 4 as our starting element for this example
```ad-example
![[Screenshots/Pasted image 20220307211951.png]]
That selected element will be called the pivot

So the elements that are left of the pivot are smaller than it and the elements to the right of the pivot are greater than it
![[Screenshots/Pasted image 20220307212120.png]]
This process is called partioning.
This process in which we select a pivot and rearrange the list that all the elements lesser than the pivot are towards the left and towards the right.

![[Screenshots/Pasted image 20220307212323.png]]
```
```ad-note
The order of the other elements doesn't really matther the only thing that does is that the elements on the left are lesser than the pivot and the right are greater than the pivot.
![[Screenshots/Pasted image 20220307212513.png]]

```

Now that we have partitions we can now break this problem up into two problems.
1. Sorting the segment of the array to the left of the pivot
2. Sorting the segment of the array to the right of the pivot.
![[Screenshots/Pasted image 20220307212721.png]]

```ad-note
We do note have to create two seperate arrays when doing the partitions of the array we can use the same one array for it as shown below:
![[Screenshots/Pasted image 20220307212851.png]]

We just need to sepcify where each partition ends so Left Parition A starts from index 0 and ends at index 2 and Right Partition A starts at index 4 and ends at index 7.
```

#### So how would we sort each array?
So we apply the partitioning method into these smaller arrays so:
```ad-example
Lets start with the left side array partition so we can pick our pivot in this we will pick 3.
![[Screenshots/Pasted image 20220307213329.png]]
Now remember before we need the left side of the pivot to be less than it and the right side to be greater. And it looks like that is already done for us in the order already.

Now that will leave us one sub-problem and work only on the segment from index 0 to 1.
![[Screenshots/Pasted image 20220307213533.png]] ![[Screenshots/Pasted image 20220307213635.png]]
Then again we will pick our pivot and apply the same rules before for the left side pivot and right side pivot.

![[Screenshots/Pasted image 20220307213652.png]]
So now we only have one sub-problem and it consists of only one element and so then our original array from index 0 - 2 is in the order of 1, 2, 3 at indices 0, 1, 2 respectively. 

```

So that was how we did for the left side now we can do the same with the right side of the pivot.

#### First Choice Pivot Rule
Now we this would be the best option for doing quicksort but lets see how this would work if we did the bad option which is *First Choice Pivot Rule. *

#### Time Complexity
First the time-complexity for this option would be $\theta$(n$^2$)

#### How would it work
For the most part it works nearly the same as if we were the choose the last element of the array as our pivot. The same rules apply for the left and right side elements of the pivot.

`````ad-example
![[Screenshots/Pasted image 20220308161818.png]]
We are going to use the first choice pivot rule onto to sort this array from lowest to highest.
The same rules apply like we did in the other example.

We are going to be choosing the first element as the pivot so in this case we pick element 72, index 0.
![[Screenshots/Pasted image 20220308162231.png]]

Then we are going to order it to where we left side of the pivot is less than the pivot and the right side is greater than it so the only elements that are greater than it is 93 and 82. The rest is less than 72.
![[Screenshots/Pasted image 20220308162350.png]]

So now we are going to partition this array into two seperate arrays 
![[Screenshots/Pasted image 20220308162552.png]]

Then we are going to be picking pivots for these two arrays and just like before we are going to be picking the first index for both.
![[Screenshots/Pasted image 20220308162727.png]]

Then we are going to be placing the other elements on the left or right side of the pivot with the same rules.
![[Screenshots/Pasted image 20220308162903.png]]

And from this we are going to continue to do the same. 
```ad-note
Later on into the example we are then met with a situation with there being only one partition. As shown below:
![[Screenshots/Pasted image 20220308163113.png]]

From here one we will only have one partition since there are no elements that are greater than our pivot so there will be no elements on the right side of it thus being only one partition.
```
We continue this process until we are up until our final few elements and we will work back our way to create our new sorted array.
![[Screenshots/Pasted image 20220308163342.png]]



`````




# References
1.

Created: 2022-03-07 20:05
Status: #idea
Tags:
# Insertion Sort
#### Theory
- Simple sorting algorithm and works the way we sort playing cards on our hands.
- That builds the final sorted array one item at a time
- Efficient for small data types 
- More efficient in practice than most simple quadratic algorithms such as selection sort or bubble sort

#### Working
Steps
1. Pick next element
2. Compare with all elements in the sorted sub-list on the left
3. Shift all the elements in the sorted sub-list that is greater than the value to be sorted 
4. Insert the value
5. Repeat unti list is sorted

#### Applying the algorithm
We will be applying the insertion sort on this array below:
![[Screenshots/Pasted image 20220307204527.png]]
So we go through the first step
1. Take 7 & insert in position 0.
```ad-example
![[Screenshots/Pasted image 20220307205549.png]]
```
2. Take 3 & insert in position 0.
```ad-example
![[Screenshots/Pasted image 20220307205934.png]]
```
3. Then we will compare 9 and 6 and we see that 6 is less than 9 so we will have to shift 6 down one spot so 9 and 6 swap. Then we compare 6 and 7 and we see that 6 is also smaller than 7 so we swap those two as well. That will leave us with taking 6 & insertting it into position 1.
```ad-example
![[Screenshots/Pasted image 20220307210540.png]]
```
4. Then we get to our last two elements of 9 and 2 where we will first compare those two first and we see that 2 is smaller than 9 and the other elements that come after so we will then all the other elements over as well. Then we will finally take 2 and insert it into position 0.
```ad-example
![[Screenshots/Pasted image 20220307210723.png]]
![[Screenshots/Pasted image 20220307210737.png]]
```


# References
1.

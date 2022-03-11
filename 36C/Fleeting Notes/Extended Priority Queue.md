Created: 2022-03-08 19:15
Status: #idea
Tags:
# Extended Priority Queue
Additonal Data Structure to track position of each key/node in the heap (the underlying array), these extended operations take $\theta$ (lg$N$) time:
- DecreaseKey(k,change)
- IncreaseKey(k,change)
- Remove(k)

#### DecreaseKey(k, change)
- Decreases the key of the target node by a specified amount
Steps:
1. Find the node using the additional data structure
2. Decrease the key as desired
3. Percolate up as long as necessary

```ad-example
Lets say we want to decrease the key 65 to the value of 21.
1. So we would first find the node
![[Screenshots/Pasted image 20220308192641.png]]
2. Then we are then going to decrease it to the value we want it to be which in this case it is 21.
3. Then we have to percolate up since the parent of the node has to be smaller than the child so in this case the parent 30 is not smaller than 21. So we move it up and check if its new parent 27 is smaller than it and no, 27 is greater so we move it up. And then finally we check if its smaller than the root node and we see that 20 is indeed smaller the the 21 so we keep it where it was.
![[Screenshots/Pasted image 20220308192949.png]]

```


### Remove(k)
The remove function can be used to remove any element not necessarily minimum.
Steps:
1. Find the node using the additional data structure
2. Remove the node
3. Replace the node with the rightmost node from the last level, to maintain structure property.
4. Percolate up or down.

```ad-example
1. Lets say we want to remove the node 21 from the binary heap. So we first look for which element we want to delete first.
![[Screenshots/Pasted image 20220308193409.png]]
2. So now we just remove the node from the heap. 
![[Screenshots/Pasted image 20220308193545.png]]
3. Now we have to replace the mode with another one and we are choosing the rightmost node from the last level. In this case it will be 98 as its on the last level and the furthest to the right.
4. So we are going to place 98 there where 21 was and now we must determine if we percolate up or down. Here we can tell that we must percolate down since 98 is going to be larger than all its children. So we go down one by one and first we ask 27 if its bigger than it and indeed it is so we swap those two. Then we ask our left child if we are greater than them yes 98 is greater than 30 and so we swap. There are no other children so 98 is where it is suppose to be.
![[Screenshots/Pasted image 20220308194057.png]]

```

### Increase Key(k, change)
Works very similar to how the decrease key works. The only difference is that increase is going to be increasing the value of the selected key and then it will be following the same steps. Instead of percolate up we are going percolate down since the bigger numbers suppose to be lower than the smaller numbers on the binary heap.
# References
1.

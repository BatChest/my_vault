Created: 2022-03-06 13:36
Status: #idea
Tags:
# Balancing in Binary Trees
Binary Tree is called a *BALANCED* binary tree, if the difference between the *HEIGHT* of left $\&$ right subtree for every node is not more than k (usually k = 1) 
```ad-note
The Height of a tree is the number of edges on the longest path between root node $\&$ and leaf node
```

```ad-note
leaf nodes usually at the lowermost bottom of trees and have no children on left or right side

```

Lets take a look at an example of calculating the Height
```ad-example
![[Screenshots/Pasted image 20220306134547.png]]
Here we are starting at the root node of the tree and then we are locating the leafs in our tree and we looking for the furthest one from the root. In this case it is node 32. Then we count the edges or lines from the root and we count 3. So our height is 3.

```
Heres another Example
```ad-example
![[Screenshots/Pasted image 20220306134809.png]]
Here again we are looking for the leaf nodes and looking the furthest most from the root node. In this case it is node 32. Then we goor to our root node and count the edges/lines to node 32. We count 3 and so our height is 3.  

```
What makes a Binary Tree Balanced?

A Binary Tree is Balanced if the difference between the *HEIGHT* of left $\&$ right subtree for every node is not more than k(usually k = 1)
Lets look at two examples for determing if a tree is *BALANCED*
````ad-example
![[Screenshots/Pasted image 20220306135419.png]]
First we usually determine the Left SubTree and the Right SubTree and root node.

So now lets focus on just the Left Sub Tree anc calculate its HEIGHT
![[Screenshots/Pasted image 20220306135654.png]]
Now we do what we did in the previous examples but this time the root node in this SubTree is 21 and the leaf nodes are 13 and 32 being the furthest most from the root. So we'll count the edges/lines and we get 2 as our Height of the Left SubTree.

Then we go the Right SubTree and repeat the same steps
![[Screenshots/Pasted image 20220306135942.png]]
This time our height is going to be just 1.

Then we'll subtract LST-RST
=2-1
=1

Since our answe is 1 then this means that it is not greater than k which is usually 1 so that makes this balanced.

But this means that we would have to do the entire process for every node.

So lets go back to the left side and calculate the height of the Left Side Tree.
![[Screenshots/Pasted image 20220306140638.png]]
Again we are just repeating the same steps as we did previously with the one difference is that 13 is a leaf node so it has no children so its height will be zero.
Then do LST-RST
= 0-1
= -1
= |-1| = 1

```ad-note
Difference between the height cannot be negative
```


````


# References
1. https://www.youtube.com/watch?v=MpGOoJtEYII&list=PLIY8eNdw5tW_zX3OCzX7NJ8bL1p6pWfgG&index=80
2. 

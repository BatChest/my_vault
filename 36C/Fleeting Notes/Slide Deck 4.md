Created: 2022-03-05 15:48
Status: #idea
Tags: [[Data Structures]]
# Slide Deck 4
### What are binary Trees?
Binary search Trees are like regular trees but just like the name says its in binary so theres a left and right side of the tree or at most two children. If it has more than two thens its not a tree.
![[Screenshots/Pasted image 20220305155240.png|300]]

### What are Binary Search Tree?
As said previously these would have at most two children. The nodes on the left side would be less than the root, while the nodes on the right side would be greater than the root.
![[Screenshots/Pasted image 20220305155628.png|300]]

### How does the Find Function work in a Binary search Tree?
It acts in the same way as a binary search but in a data structure.
![[Screenshots/Pasted image 20220305155902.png|300]]

#### When We cant find the desired element
![[Screenshots/Pasted image 20220305160121.png|300]]

#### Why is the worst case runtime for the find function linear?
The reason for this is that the worst shaped tree would have nodes going down in a sequential order as shown below:
![[Screenshots/Pasted image 20220305160416.png|300]]

Then it would start going down that list one by one until it finds the desired element.

#### How does the Insert Function work in BST?
The steps it takes is:
First, to do the find function to find a location to place the new element
Second, Create the new node or link.
![[Screenshots/Pasted image 20220305160859.png|550]]

#### Deletion for a BST
The Steps we do to delete an element as follow:
First, we find the element we want to delete
Next, We Remove it but that requires more steps
	First, If the target is a leaf, we're done
	Otherwise, theres more work to that

This leads to a whole other sort of steps and things start to get more complicated so there might a whole seperate notes on that
But the basics of it goes like this:
![[Screenshots/Pasted image 20220305161547.png]]

Replacement with deletion works like this:
1. Max of the left subtree.
	-That max's left subtree is moved up to max's old spot
2. The Min of the rightsubtree.
	-That min's right subtree is moved up to min's old spot.
This would look like this:
![[Screenshots/Pasted image 20220305161846.png]]
![[Screenshots/Pasted image 20220305161907.png]]

```ad-note
All three functions in their worst time complexity are all in linear($\theta$($n$)) since the worst tree will be in a sequential line down so it iterates through each element 
```

# References
1. https://canvas.ucdavis.edu/courses/632689/files/folder/ECS%2036C%20Lecture%20Slides?preview=15556651

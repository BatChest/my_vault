Created: 2022-03-06 13:01
Status: #idea
Tags:
# AVL Insert Function
To Insert we do the same as a [[Slide Deck 4|BST insertion]].
Then we are going to update the height and balance of the partent of that leaf:
* New Node is left child -> increment parent's balance factor
* Else -> decrement

Update parent's parnet
* Update root
* Update node whose balance factor becomes zero
* Update node that becomes unbalanced; rebalancing occurs

```ad-example
![[Screenshots](/Screenshots/Pasted image 20220306132637.png)

```
How about one if we adjust's parent's balance factor to zero, not adjusting ancestors.
```ad-example
![[Screenshots/Pasted image 20220306132755.png]]

```
Eventually we are going to get going into rebalancing when we do our opertations such as deletion and insertion. This will lead to having to do some [[AVL Tree Rotations|Rotations]].


# References
1. https://www.youtube.com/watch?v=f0BplF93TIA&list=PLIY8eNdw5tW_zX3OCzX7NJ8bL1p6pWfgG&index=83
2. https://canvas.ucdavis.edu/courses/632689/files/folder/ECS%2036C%20Lecture%20Slides?preview=15680237
3. 

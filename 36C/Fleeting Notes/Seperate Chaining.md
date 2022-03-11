Created: 2022-03-10 16:51
Status: #idea
Tags:
# Seperate Chaining
- Each bucket contains a linked list
- Hash function to determing which list to check
```ad-example
![[Screenshots/Pasted image 20220310165246.png]]
We have a hash table and the buckets have linked list pointing to another bucket in which we are able to store more values.

![[Screenshots/Pasted image 20220310165328.png]]
So when we insert 53 we dont have to worry about being another number being there instead we can just store it into the linked list while still keeping it at the index we intended to insert it in.
```

- Linked List are not the only elements that can used for storing these numbers as we can use trees to store them but since elements per bucket is small and easier to be used.
```ad-example
![[Screenshots/Pasted image 20220310165554.png]]

Here we can use a binary tree to store the elements and would do the same function of using a linked list for storing the numbers.
```

### Analysis
- load factor (λ = n/m): ratio of number of elements in hash table to table size
- Average length of list is λ
- Search: find list-to-traverse (takes constant time) and traverse said list
- Load factor is more directly important than table size



# References
1.

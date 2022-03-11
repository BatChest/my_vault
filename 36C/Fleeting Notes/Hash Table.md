Created: 2022-03-10 16:32
Status: #idea
Tags:
# Hash Table
- Supports less operations than self-balancing BST for speed; sorted order of elements isn't maintained
- Underlying implementation is array of $m$ slots/buckets
- Location of element is influenced by its key
- Maps keys to some number in range [0,m-1].

```ad-example
The keys are strings
Hash function 
- Maps "Bob" to 1 or Bob hashes to 1
- Maps "Julia" to 3 or Julai hashes to 3
- Maps "jake" to 4 or Jake hashes to 4.

![[Screenshots/Pasted image 20220310163532.png]]
```

#### Hash Functions
- Possible keys usually larger than $m$(number of slots and buckets)
- Want to distribute keys as evenly as possible
- Assume keys are always integers for now -> typical hash function is hash(x) = x % m. 

```ad-example
Here we going to use insertion function to insert 14.
![[Screenshots/Pasted image 20220310163906.png]]
We have a blank hash table and then we insert 14 which picks its spot by doing 14 % 10 = 4. Because we have 4 as our remainder we would place 14 at index 14 in the hash table. 

![[Screenshots/Pasted image 20220310164008.png]]
Then we are inserting 40 in which we do the same as we did before. So 67 % 10 would give us the remainder of 7 so we place 67 at index 7 on the table. 

Then for 40 we do the same thing and since we aren't given a remainer when modding 40 by 10 we place it at index 0.
```
For the find function we do the same thing by modding the number we are looking for by the total amount of slots/buckets and getting a remainder and then checking that index if our number is there or not.
```ad-example
Here we are looking for 97 in our hash table so we do 97 % 10 and we are given the reamainder of 7 so we look at index 7 and we are able to find 97.
![[Screenshots/Pasted image 20220310164425.png]]
```

Lets look for one example that is not able to find the number we are looking for. 
```ad-example
This time we are looking for 46 and so we do 46 % 10 and we get the remainder of 6. So we look at index 6 and so we look there are it is not there.

![[Screenshots/Pasted image 20220310164629.png]]

```



# References
1.

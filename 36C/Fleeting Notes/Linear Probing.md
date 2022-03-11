Created: 2022-03-10 17:05
Status: #idea
Tags:
# Linear Probing
- If cant key at a bucket, try to place at next bucket(wraparound). If that doesn't work, try next bucket. And so on...
````ad-example
We have a blank hash table and we insert 11.
![[Screenshots/Pasted image 20220310170655.png]]

Then we insert 30 next and so we place it at 2 since 30 % 7 is 2.
![[Screenshots/Pasted image 20220310170922.png]]

After we insert 53 in which we do 53 % 7 which gives us 4 so we have a collision which because of linear probing we are moving up on bucket to place 53.
![[Screenshots/Pasted image 20220310171023.png]]

If we continue to place more values then we would continue to do linear probing for every collision

![[Screenshots/Pasted image 20220310171112.png]]
So we insert 74 and get 4 again so we move up one bucket and see that is also taken so again we move up by 1 and see if its empty and it is so we place 74 there. 

Now here is the first example of wrapping around since we insert 12 which gives us 5 and since we have 53 and index of 5 we move up one bucket and see that one is not empty so we start at the beggining of the hash table and check if index 0 is empty and it is.
![[Screenshots/Pasted image 20220310171317.png]]

We will continue going by one bucket at a time until we find an empty slot so when we insert 20 we will continue checking empty slots one at a time.
![[Screenshots/Pasted image 20220310171426.png]]

```ad-note
In case you were wondering the λ would be 6 elements in our hash table over 7 total buckets in the hash table which makes it λ=6/7 at end. (this is bad)
```
````
How about when we are using the find operation we are basically doing the same thing as before just keep going through each bucket one at a time until we find the number we are looking for or reach an empty slot.
```ad-example
![[Screenshots/Pasted image 20220310182426.png]]
![[Screenshots/Pasted image 20220310182435.png]]
```

A failed operation would be when we are looking for a number but we aren't able to find it.
```ad-example
![[Screenshots/Pasted image 20220310182537.png]]

![[Screenshots/Pasted image 20220310182544.png]]
```

### Deletion
This is an example of the bad way of deletion.
```ad-example
Lets say we have want to delete a number and so we delete it and then we want to find another number this is in the hash table but when we mod it by the number of slots of the table we get the index of the number that was previously deleted. In reality the number we are looking for was actually in the table but was in the slot next to it.
![[Screenshots/Pasted image 20220310182914.png]]
```

### Lazy Deletion(The Good Way)
- We mark that we deleted the selected element instead of actually deleting it hence why its called lazy.
- We aren't actually deleting the element
- A lazily deleted node can be replaced
```ad-example
![[Screenshots/Pasted image 20220310183233.png]]
Here we aren't actually deleting 11 just marking that it is deleted since if we want to look for 53 the operation wont fail since there is still a number in that slot instead of it being empty.

![[Screenshots/Pasted image 20220310183330.png]]

As we said earlier wa can replace the lazily deleted number so if we insert another number and it gets placed at the same index of the deleted number then it just replaces it.
![[Screenshots/Pasted image 20220310183416.png]]
```

### Weakness
- Primary Clustering: Blocks of nearby occupied buckets tend to form
- New key may take several collision resolution attempts (and then adds to the cluster)

# References
1.

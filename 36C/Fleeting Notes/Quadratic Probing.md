Created: 2022-03-10 18:36
Status: #idea
Tags:
# Quadratic Probing
- Eliminates primary clustering issue
- If cant place bucket at $u$, try to place at bucket 1$^2$ = 1 after that one. If doesn't work, try to place bucket at 2$^2$ = 4 after $u$. If that doesn't work, try to place at bucket 3$^2$ = 9 after u. This continues and wrap arounds as well
- Another way of thinking: Check next bucket, then check 3 buckets later, then check 5 buckets later, then 7 buckets later, etc

```ad-example
![[Screenshots/Pasted image 20220310183952.png]]
So we insert like we usually do and we have a collision so we then do move up one slot and since its empty we place it there.

Now lets insert another one
![[Screenshots/Pasted image 20220310184046.png]]
Now we insert again and theres another collision so we move to the next slot and its already taken and instead of going one by one we go up by three slots. We get to index 6 and its empty so we can insert our number there.

Now lets say we insert another number and after we move up three slots its already taken so then we move up five slots. 
![[Screenshots/Pasted image 20220310184702.png]]
When we move up five slots from index 6 we land onto index 4 and thats empty so we insert it there.
```
Lets keep adding onto the previous example
```ad-example
![[Screenshots/Pasted image 20220310185052.png]]
We insert 10 and we get 3 we mod it by the total slots and theres a collision. So first we move up one slot to see if its empty and its not. So we go up by three slots and we land on index 0 and we see that theres nothing there so we insert it there.
![[Screenshots/Pasted image 20220310184849.png]]

### Now lets delete from this hash table
We'll delete 23 and so we look for 23 by doing 23 % 10 which we get 2. So we look at index 2 and see that 16 is there so we go up by one slot and check if 23 is there and it is. So we mark 23 as delete but we dont delete it.
![[Screenshots/Pasted image 20220310185242.png]]

### Find Operation
We want to find 44. So we do 44 % 7 and get 2. We go to index 2 and see that 16 is there so we move up one slot. There we see taht 23 is there but deleted so we continue looking for 44. Since we are doing quadratic probing the operations behave the same way by going up by three slots. So we go up 3 slots and land on index 6 where 37 is at so we keep going. This time we move up 5 slots and we land on index 4 and there is 44.
![[Screenshots/Pasted image 20220310185540.png]]
```

### Analysis
- For Linear Probing, high λ degraded preformance
- For Quadratic Probing, λ > 1/2 can make it impossible to find empty empty buckets
- If table size not $prime$, can happen even with λ $\le$ $\frac12$. 
```ad-example
If insert 8 into below table, will check indices 0,1, and 4 forever
![[Screenshots/Pasted image 20220310190220.png]]
```
- Can prove that if table is half empty and table size is prime, guaranteed to find empty bucket
- Vulnerable to secondary clustering : elements hashed to same location will probe same buckets



# References
1.

Created: 2022-03-10 19:06
Status: #idea
Tags:
# Double Hashing
- Eliminate secondary clustering issue
- Requires second hash function h$_2$($x$)
- If can't place key $k$ at bucket, try to place h$_2$($k$) spots later. And 
	so one and so forth. (wrap around when needed)
- Slower than quadratic in practice, because second hash function

```ad-example
![[Screenshots/Pasted image 20220310190912.png]]
```

Now lets do some operations
```ad-example
We will start by inserting 32 into the hash table

first we check 32 % 7 and that gives us 4. Then we do h$_2$(32) = 32 % 5 = 2. So when we first did modding of the hash table we got 4 so we try inserting at index 4 and its filled so we go back and try to do it 2 slots over and see if thats empty. We land at index 6 and we see that its filled with 34 in it. We wrap around and go by two slots again and we land on index 1 and we see that its empty, so we can insert it there.

![[Screenshots/Pasted image 20220310191437.png]]

Now lets insert 43 and first we do 43 % 7 = 1. So we try inserting it at index 1 and its filled with 32. Next we use the hash function 43 % 5 = 3. 
So then we move up 3 slots and we land onto index 4 where 11 is there. Then we go up 3 slots again we land on index 0 which is empty so we are able to place it there. 

![[Screenshots/Pasted image 20220310191908.png]]
```

# References
1.

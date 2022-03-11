Created: 2022-03-10 19:21
Status: #idea
Tags:
# Rehasing
- If λ is too high, we can rehash
- Steps: (let $m$ be old table size, $m'$ new table size)
	1. Create new table of size $m'$ = $nextPrime$, where $nextPrime$(x) returns lowest prime number above $x$
	2. Insert each element in old table into new table, using new hash function, $h_1$($k$) = $k$ % $m'$.

```ad-example
- Rehash when λ $\ge$ $\frac12$.
(We are using linear probing for this example)
![[Fleeting Notes/Screenshots/Pasted image 20220310195207.png]]
So we would first need to calculate λ and we get 3 and thats bigger than $\frac12$ so we rehash.

To rehash we do (2*7) since the old table had 7 slots and then we get 14 and then we must find the lowest prime number above 14 and the closest prime number is 17 so we create a new table that is 17 slots.

![[Fleeting Notes/Screenshots/Pasted image 20220310195818.png]]

After we rehash we can insert back in the old numbers and new ones

```

# References
1.

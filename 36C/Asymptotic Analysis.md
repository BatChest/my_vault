# Asymptotic Analysis
Created: 2022-04-27 17:59

## Loops
```cpp
for(i = 1; i <= n; i++)
	//statement
```
- Loop executes $n$ times so it'll be $O(n)$

## Nested Loops
```cpp
for(i = 1; i <= n; i++) {
	for(j = 1; j <= n; j++) {
		//statement 
	}
}
```
- Outer loop executes $n$ times
- Inner loop executes $n$ times as well
- Total time would be $n * n = O(n^2)$

## Consecutive Statements
```cpp
int x = 2;
int i;
x = x+1;

for(i = 1; i <= n; i++) {
	//statement
}
	for(i = 1; i <= n; i++) {
		for(j=1; j<=n; j++) {
			//statement
		}
	}

```
- The first three lines are going to execute once each so its total is 3 units
- The first for loop will execute n times
- The nested for loops will each execute n times and combined we have $n*n$ or $n^2$
- Total time of this entire snippet will be $n^2+n+3 = O(n^2)$

## If Statements
```cpp
scanf("%d", &n);
if(n == 0) {
	//statement
}
else{
	for(i = 1; i<=n; i++)
		//statement
}
```
- For **if part** the n == 0 takes constant time
- the statement inside that if statement takes constant time
- So total time would be 1+1 = $O(1)$
- The **For else part**, n== 0 takes constant time
- Statement get executed $n$ times
- Total time: $1+n=O(n)$
- The overall complexity of this snippet is: $O(n)$

## Logarithmic Complexity
$log_2(8) = 3$
Above us tells us "how many times, 2 has been multiply by itself in order to obtain the value 8."
So that is why the answer is 8.
Logarithmic time complexity is achieved when the problem size is cut down by a fraction 
### Time Complexity
```cpp
for(i=1; i <= n;)
{
	//statement
	i = i*2;
}
```
For the loop is acting more a of an iteration so we break this down by each iteration of the loop
Iter1	 Initially i = 2 	$2^0$
Iter2				i = 2	$2^1$
Iter3 i = 4 $2^2$
Iter4 i = 8 $2^3$
Iter5 i = 16 $2^4$
this continues so we can conclude that this would become:
iterk i = n = $2^{k-1}$
So we would have $n = 2^{k-1}$
Then we can make the assumption that:
$k-1=log_2n = k = log_2n+1 = O(log_2n)$

### Example
```cpp
for(i = 1; i <= 32;)
{
	printf("Hello");
	i = i*2;
}
```
- $K = log_{2} 32 + 1= 6$

### Example 2
```cpp
for(i = n; i>= 1;)
{
	//statement
	i = i/2;
}
```
- If we go through the process of the going through each iterator we can see the complexity of each one
- Looks look inside the for iterator, we have i = i/2;
- We can conclude that i = $\frac{n}{2^n}$. The n would represent the number of each iteration starting with zero
- so we would have $\frac{n}{2^{k-1}} = 1$
- which we simplify into $n = 2^{k-1}$
- Then we can conclude that $k-1=log_2n -> k = log_2n+1 -> O(log_2n)$

## References
1.

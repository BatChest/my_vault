# Mat21c Last Lecture
Created: 2022-03-09 15:12
### Geometric solution 
x$^2$ +y$^2$ = , x+y=constant = f(x+y)
x$^2$ +y$^2$ is constraint

x+y = 1
x+y= -1
x+y= 0

The level curves have to touch the constraint curves
```ad-example
![[Pasted image 20220309151704.png]]
at extreme values we can see that the level curves of f are tangent the constraints.
```

### Algebraic way
F(x,y) subject to g(x,y) = c is maximized/minimized at (x$_0$, y$_0$) then
- f is tangent to g(x,y) = c at (x$_0$, y$_0$)
```ad-example
![[Pasted image 20220309152042.png]]
```
- f(x$_0$, y$_0$) parallel to g (x$_0$, y$_0$) with g(x$_0$, y$_0$) doesn't equal 0
- f(x$_0$, y$_0$) = $\lamda$ g (x$_0$, y$_0$) with g(x$_0$, y$_0$) doesn't equal 0. 
```ad-example
![[Pasted image 20220309152437.png]]
The lamda is the langrage multiplier
```

### Critical Points for constraint problems
Suppose f(x,y), g(x,y) are differentiable functions.
Suppose(x$_0$, y$_0$) is called a critical point for max/min f(x,y) subject to g(x,y) = c if
- g(x$_0$, y$_0$) doesn't equal zero 

### How can you tell if a critical point is max or min
- Given at the contours
- Second derivative test:
	- Define L(x,y,lamda) = f(x,y) - lamda g(x,y)
	- Compute

```ad-example
![[Pasted image 20220309153029.png]]
```
- If -H(x$_0$, y$_0$, lamda) > 0, (x$_0$, y$_0$) is a local min
- If -H(x$_0$, y$_0$, lamda) < 0, (x$_0$, y$_0$) is a local max
````ad-example
consider f(x,y) = -4(x+y) subject ti x$^2$ + y$^2$ = 1
(A) show that lamda = +- 2$sqrt$ 2
(B) Find extreme values

First lets do part A.
x$^2$ + y$^2$ = g
```ad-note
lamda cannot equal to zero
```
![[Pasted image 20220309153635.png]]

These are the critical points
![[Pasted image 20220309153804.png]]  ![[Pasted image 20220309154044.png]]
The top is the max point and the bottom is the min

![[Pasted image 20220309154026.png]]
````

```ad-example
max/min 4x$^2$+y$^2$ subject to xy = 1. Geometric solution.
g = 1, y=1/x
![[Pasted image 20220309155358.png]]

max/min 4x$^2$+y$^2$ subject to xy = 1. Show that lamda = 4 is the langrange multiplier.
![[Pasted image 20220309155502.png]] ![[Pasted image 20220309155643.png]]
![[Pasted image 20220309155722.png]] ![[Pasted image 20220309155807.png]]
![[Pasted image 20220309155817.png]]
![[Pasted image 20220309155917.png]]


```

## References
1.

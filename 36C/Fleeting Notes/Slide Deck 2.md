Created: 2022-03-05 15:08
Status: #idea
Tags: [[Data Structures]]
# Slide Deck 2

How would one use asymptotic notation as a placeholder for an anonymous function?

Based on these examples we can see that the way we are putting a placeholder for these anonymous functions is be grabbing either theta or big O depending if its in the function and then we would use that. Then based on the examples we are going to use the biggest variable in the function.

```ad-example
![[Screenshots/Pasted image 20220305154424.png]]
- In the first example we have Big $\theta$ in our function so we would be using that for our placeholder. Then we look for the biggest variable and in this case we have n$^2$ as the biggest one so our placeholder would be $\theta$(n$^2$).
```

```ad-example
![[Screenshots/Pasted image 20220305154655.png]]
- Here we are given tow functions so lets look at the first one. We have Big $\theta$ again in our equation so we can use that for our placeholder. Then we are going to be using the biggest variable in this case $n^4$. That makes the placeholder for that function be $\theta$($n^4$).
- For function f$_3$ we have big O being used so that will be used for the place holder. Then we are going to look for the biggest variable and in this case it is $n^2$. That will make f$_3$(n) be O($n^2$)
- Now if we are only asking for f$_3$ then we will still use Big O but instead just use 
```

Example 3:
![[Screenshots/Pasted image 20220305154727.png]]





# References
1.  https://canvas.ucdavis.edu/courses/632689/files/folder/ECS%2036C%20Lecture%20Slides?preview=15312740


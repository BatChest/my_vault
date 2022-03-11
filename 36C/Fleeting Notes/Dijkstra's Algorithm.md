Created: 2022-03-10 13:52
Status: #idea
Tags:
# Dijkstra's Algorithm
- Single Source Shortest Path (SSSP) algorithm for graphs with non-negative edge weights
- All edges must contain non-negative edge weights
- Basically looking for the shortest path from the starting point so lets look at a quick example


![[Fleeting Notes/Screenshots/Pasted image 20220310140404.png]]
Lets say we are given this graph and we want to know the shortest path from $E$ to each other vertices in the graph

We would have a table:
Since we are looking for paths from $E$ we will have the distance of $E$ be zero and since it has no parent it not have one. Since there is only one way to $E$ which is just $E$ then this will finilized. 

| V      	  | Distnace[v] |Finalized[v]| Parent[v]|
| :---        |    :----:   |    :----:  |    ---:	|
| A      	  |14           |False       |D 		    |
| B           |             |            |		    |
| C			  |			    | 	         |		    |
| D           |             |            | 		    |
| E           |0             | True           |N/A		    |
| F			  |			    | 	         |		    |
- So would first look at the shortest distnace to get to $A$ from $E$. We see that there are row possible paths we can take on is 14 total from $D$->$A$ or going straight to $A$ with a distance of 15. We are going to make this false for finalized since the shortest path us go through $D$ to get to $A$ instead of going directly to $A$ from $E$. The parent is going to $D$ since that would be last place we take to get to $A$. 

- Next we look for the shortest path to B which in this case would be infinty since there is only one visable path to get to $B$ and we aren't sure if there other vertices going towards $B$ so we deem it infinity. And since we have its distance infinity then we can't be sure if there is a Parent for it so we put in None. And since we aren't sure if there are other vertices we cant finalized this so we would place it as False.

| V      	  | Distnace[v] |Finalized[v]| Parent[v]|
| :---        |    :----:   |    :----:  |    ---:	|
| A      	  |14           |False            |D 		    |
| B           |infinty      |False            |None		    |
| C			  |			    | 	         |		    |
| D           |             |            | 		    |
| E           |0            | True       |N/A		    |
| F			  |			    | 	         |		    |

- Now we are trying to see the shortest path to get to $C$. There are two ways we can get to $C$ from $E$. One is is going directly to from $E$ with the path length of 2. The other path we can take is go to $F$ to $C$ with a total length being 9. Since 2 is less than 9 we will take the path going directly to $C$ as our shortest path making the distance 2. This path is going to be finalized since this path is going directly to C and we aren't going to another letter to get to $C$ so we can make this True. The parent of this path would be $E$ as that was the letter we can from before getting to $C$. 

| V      	  | Distnace[v] |Finalized[v]| Parent[v]|
| :---        |    :----:   |    :----:  |    ---:	|
| A      	  |14           |False       |D 		|
| B           |infinty      |False       |None		|
| C			  |2			|True 	     |E		    |
| D           |             |            | 		    |
| E           |0            | True       |N/A		|
| F			  |			    | 	         |		    |

- With $D$ we can see there are two paths to get there first lets look from going directly to $D$ from $E$. That will be the length of 4. Then we can take the path from $E$ ->$A$ -> $D$ but the total length would be 25 so we must use $E$->$D$ as the shortest path which is 4. This would be finalized since we are not going through other letters to get to $D$ so this makes it TRUE.  Since the letter $E$ was the last place we were before reaching $D$ then that will make $E$ its parent.

| V      	  | Distnace[v] |Finalized[v]| Parent[v]|
| :---        |    :----:   |    :----:  |    ---:	|
| A      	  |14           |False       |D 		|
| B           |infinty      |False       |None		|
| C			  |2			|True 	     |E		    |
| D           |4            |True        |E 		|
| E           |0            | True       |N/A		|
| F			  |			    | 	         |		    |

- Finally we have $F$ and there are two possible paths we can take to get to it. One is from $E$ -> $C$ -> $F$ which is the length of 5. The second one is from $E$ -> $F$ which is a length of 6. The path of E$ -> $C$ -> $F$ is shorter so we would use that since its 5. This path would not be finalized as we have to go through $C$ first to get to $F$ so it would be False. Since the last letter we were at before reaching $F$ was $C$ so that would make it the parent. 

| V      	  | Distnace[v] |Finalized[v]| Parent[v]|
| :---        |    :----:   |    :----:  |    ---:	|
| A      	  |14           |False       |D 		|
| B           |infinty      |False       |None		|
| C			  |2			|True 	     |E		    |
| D           |4            |True        |E 		|
| E           |0            | True       |N/A		|
| F			  |5			|False	     |C		    |


# References
1.

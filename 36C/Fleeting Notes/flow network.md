Created: 2022-03-08 17:07
Status: #idea
Tags:
# flow network
- Directed Graphs or flow graph
- edge has certain capacity which can receive a certain amount of flow
```ad-example
![[Screenshots/Pasted image 20220310131910.png]]
```
- Source node generate traffic/flow
	- no incoming edges
- Flow running through an edge must be less than or equal to the capacity

- Sink nodes absorb traffic/flow
	- no outgoing edges.

- Internal nodes: not source or sink nodes
- For simplicity, we assume one source and one sink.


```ad-note
![[Screenshots/Pasted image 20220309213531.png]]
The source is the starting node and the sink is the ending node just for clarification
```
```ad-example
![[Screenshots/Pasted image 20220308171040.png]]
```
### Flow
- Same node and edge directions as flow network, but edge weights specify current flow.
- Constraints:
	- Capacity condition
	- Conservation condition

```ad-example
![[Screenshots/Pasted image 20220308172245.png]]
```
#### What can't be a flow?
```ad-example
![[Screenshots/Pasted image 20220308172340.png]]
```


To find the maximum flow, Ford-Fulkerson method repeatldly finds argumenting paths thorught the residual graph and augments the flow until no more augmenting paths can be found. 

### Augmenting Path
- path of edges in the resudual graph with unused capcity greater than zero from the source $s$ to the sink $t$
```ad-example
Here the orange path highlights a potenital augmenting path
![[Screenshots/Pasted image 20220310132337.png]]


![[Screenshots/Pasted image 20220310132546.png]]
In the path above, the bottleneck is the "smallest" edge on the path. We use this to augment the flow along the path.

Smallest remaining capcaity of any edge along the augmenting path is:
min(10-0, 15-0, 6-0, 25-0, 10-0) = min (10,15,6,25,10) = 6
```
### What does it mean to Augment the Flow?
- updating the flow values of the edges along the augmenting path. 
- forward edges, this means increasing the flow by the bottleneck value.
```ad-example
![[Screenshots/Pasted image 20220310132842.png]]
- Here we have increased the flow of each edge along the augmenting path by exactly six units we're not done yet. 

![[Screenshots/Pasted image 20220310133133.png]]
- When augmenting th eflow along the augmenting path, you also need to decrease the flow along each residual edge by the bottleneck value. 
- These dotted lines are residual edges and exist to undo bad choices or paths which do not lead to a maximum flow. 
```
```ad-note
![[Screenshots/Pasted image 20220310133554.png]]
You can think of every edge in the original graph as having a residual edge with a flow/capacity of 0/0 which is not usually shown
The residual graph is the graph which also contains residual edges. In general, when mentioning flow graph we mean residual graph.
```

### Residual edges have a capacity of 0? Isn't that forbidden? How does that work?
- Think of remaining capacity of an edge $e$ as: e.capacity - e.flow
This ensures that the remaining capacity of an edge is alwatys non-negative (even if the flow can be negative)

```ad-example
![[Screenshots/Pasted image 20220310133952.png]]
Bottleneck is 4 since the min of the remaining capcacity on the augmenting path is 4:

min(10-6, 15-6, 10-0) = min(4, 9, 10) = 4

Heres another augmenting path from the source to the sink
![[Screenshots/Pasted image 20220310134323.png]]
The bottleneck value is 6 since the smallest remaining capacity amongst the edges of our augmenting path is:
min(10-0, 0- -6, 10-4) = min(10,6,6) = 6


```








# References
1. https://www.youtube.com/watch?v=LdOnanfc5TM



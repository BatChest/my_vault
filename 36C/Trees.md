# Trees
Created: 2022-04-13 20:17
### Why Trees?
- For large sets of items, linear complexity of linked lists and arrays for some operations is prohibitive 
- Need for a new search data structure for which the **average** time of most operations is $O(lgN)$

### Recursive Definition
- A collection of nodes starting at a root node.
- Where each node is connected to zero or more child nodes via edges 
- With the constraints that no reference is duplicated, and no node points back to the root

### Terminology
#### Root
- Root node is the top node
![[Pasted image 20220413202410.png|400]]
- There can only be one root node
#### Edge
- An edge is a connecting link between two nodes
- Highlighted in blue
![[Pasted image 20220413202556.png|350]]
	- Tree compose of N nodes has N-1 edges
#### Parent
- A parent node which is the direct predecessor of another node.
![[Pasted image 20220413202715.png|367]]

#### Child
- A node which is direct descendant of another node
![[Pasted image 20220413203057.png|400]]
- All nodes in a tree are all child nodes except for the root node

#### Descendant/Ancestor
- Nodes connected by more than one edge
![[Pasted image 20220413203322.png]]

#### Siblings
- Are all nodes descending from the same parent
![[Pasted image 20220413203538.png]]

#### Leaf 
- Node in which has no child
![[Pasted image 20220413203603.png]]
#### NIL
- The absence of child nodes is sometimes represented as NIL
- Usually represented with NULL pointers
![[Pasted image 20220413203647.png]]

#### Internal Node
- A node in which has at least one child
![[Pasted image 20220413203726.png]]

#### Degree
- A node is the number of its children 
- Leaf node has always a degree of zero
- The degree of a tree is the maximum degree of any of its nodes
![[Pasted image 20220413203858.png]]

#### Level
- The level of a node is one greater than the level of its parent, knowing the level of the root node is 1.
![[Pasted image 20220413204706.png]]

#### Paths
- A path is a sequence of nodes and edges connecting a node with a descendant 
- The length of the path is the number of edges composing it
![[Pasted image 20220413204732.png]]

#### Depth
- The depth of a node is the path length from the root to this node.
- The depth of root is zero
- The depth of a tree is equal to the depth of the deepest leaf
![[Pasted image 20220413204835.png]]

#### Height
- The height of a node is the length of the longest path from a leaf to this node
- All leaves are at height zero
- The height of a tree is equal to the height of the root the deepest leaf (which is always equal to the depth of the tree)
![[Pasted image 20220413205012.png]]

#### Subtree
- A subtree consists of a child node and all of its descendants
![[Pasted image 20220413210608.png]]

#### Typical Implementations
##### Array of Children 
```cpp
template <typename T>
class Tree<T> {
	struct Node {
		T item;
		std::unique_ptr<Node> children;
		
	};
	std::unique_ptr<Node> root;
	...
}
```
###### Characteristics
- Most intuitive representation but... 
- Node degrees are not necessarily known in advanced for the construction
- Can lead to waste of space

##### Linked list of siblings
```cpp
template <typename T>
class Tree<T> {
	struct Node {
		T item;
		std::unique_ptr<Node> first_child;
		std::unique_ptr<Node> next_sibling;
	};
	std::unique_ptr<Node> root;
	...
}
```
###### Characteristics
- Adaptable to any degree
- Predictable memory complexity


## References
1.

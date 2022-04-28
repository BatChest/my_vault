# Binary Tree
Created: 2022-04-23 11:25

### Definition
- A type of tree in which node has at most two children
	- Usually referred to as left child and right child

### Types
#### Full Binary Tree
- In a full binary tree every node has either 0 or 2 children
- ![[Pasted image 20220423112855.png|300]]

#### Complete Binary Tree
- Every level except possibility the last one, is completely filled and all nodes in the last level are as far left as possible
- ![[Pasted image 20220423113038.png|350]]

#### Perfect Binary Tree
- All internal nodes have two children and all leaf nodes have the same depth.
- ![[Pasted image 20220423113134.png|350]]

### Traversal 
- Algorithms require all nodes of a binary tree to be visited and their contents processed or examined 
	- Printing, searching, updating etc

- Unlike linear data structures(arrays, linked lists), trees do not inherently have a linear order in which they can be traversed. 
- ![[Pasted image 20220423113424.png]]

#### Traversal Types
![[Pasted image 20220424155928.png|300]]
##### Depth First Order
- From root down to leaves
- General Reversal pattern
- From a node N:
	- (N) Process N itself 
	- (L) Recurse on N's left subtree
	- (R) Recurse on N's right subtree
```ad-note
These steps can be done in any order
```
![[Pasted image 20220424160054.png|300]] ![[Pasted image 20220424160114.png|300]] ![[Pasted image 20220424160139.png|300]]

##### Breadth First Order
- Level Order
- Visit every node on a level before going to a lower level
- ![[Pasted image 20220424160301.png|300]]

### Binary Search Tree
- Each node contains one comparable $key$ 
- Each node's key is greater to any key stored in its left subtree
- Each node's key is less than any key stored in its right subtree

#### Typical API
```cpp
// Return whether @key is found in tree
bool Contains(Const K& key);
// Return max key in tree
const K& Max();
// Return  min key in tree
const K& Min();
// Insert @key from tree
void Remove(const K &key);
// Print thee in order
void Print();
```
Other typical methods are:
- Floor(key): FInd largest key smaller or equal to given key
- Ceil(key): Find smallest key greater or equal to given key
- Rank(key): Find key rank in collection

#### Remove a Node
##### Lazy Node Deletion
- We dont actually delete the node, instead we just mark the node that we "deleted"
	- Upon later insertion of the same key, node can easily be re-enabled

##### Actual Node Deletion 
3 Scenarios
- Leaf Node, child with no node
	- ![[Pasted image 20220424173828.png]]
	- We simply remove node to be deleted from the tree
	- ![[Pasted image 20220424174205.png|250]] ![[Pasted image 20220424174218.png|250]]
- Internal Node with one child
	- ![[Pasted image 20220424173856.png]]
	- Replace node with its child
	-   ![[Pasted image 20220424174249.png|250]] ![[Pasted image 20220424174319.png|250]]

- Internal node with two children
	- ![[Pasted image 20220424173926.png]] 
	- Call D Node to be deleted 
	- Find min node in D's right tree
		- D's successor key value
	- Copy min node's key into D
	- Recursively delete min node
	- ![[Pasted image 20220424174517.png|250]] ![[Pasted image 20220424174529.png|250]]
	
#### Complexity Analysis
##### The Good
- Running time of all operations is $O(d)$
	- Apart from traversal, which is necessarily $O(N)$

- Where $d$ is the depth of the accessed node
But tree shape depends on order of insertion:
-	At best, if tree is complete, its height is $O(lgN)$
-	On average, if keys are inserted in random order, the height is still proportional to $O(lgN)$ 

##### The Bad
- Deletion tend to displace nodes from the right subtrees to the left subtrees
- Trees becomes unbalanced and depth tends towards $O(\sqrt(N))$
Some solutions 
- Avoids/forbid deletions
- Alternate picking min node in right tree with max node in left tree when deleting nodes with two children
- 
##### The Ugly
Worst Case Scenario
- Insertions of ordered values
- Complexity for all operations becomes $O(N)$ ![[Pasted image 20220424180438.png|250]]

#### Final thoughts
- Big disparities depending on shape of BST
##### Average Running Time
![[Pasted image 20220424180551.png]]

##### Worst Case Running Time
![[Pasted image 20220424180610.png]]
##### Solution 
- Make BST always balanced 
	- Each node has about the number of descendants in its subtree as in its right subtree
	- Guarantee logarithmic performance for all operations
- Such Binary Search Trees are called self-balancing 
	- AVL trees, Red-Black trees, etc  









## References
1.

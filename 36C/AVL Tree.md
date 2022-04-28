# AVL Tree
Created: 2022-04-26 22:48

## Implementation 
### Data Structure
- Based on Binary Search Tree and unchanged for all query methods
	- Contains(), Min(), Max()
- Node structure increased to contain the height information
- A few extra internal methods for self-balancing purposes
```cpp
template <typename T>
class AVL {
	struct Node{
		T key;
		int height;
		std::unique_ptr<Node> left;
		std::unique_ptr<Node> right;
	};
	std::unique_ptr<Node> root;
	
	//Helper methods for self balancing
	int Height(Node *n);
	void RotateRight(std::unique_ptr<Node> &ptr);
	void RotateLeft(std::unique_ptr<Node> &ptr);
	void Retrace(std::unique_ptr<Node> &n);
};
```

```cpp
template <typename T>
int AVL<T>::Height(NOde *n) {
	//NIL nodes
	if (!n)
		return -1;
	//Regular nodes
	return n->height;
}
```
### Right Rotation
```cpp
template <typename T>
void AVL<T>::RotateRight(std::unique_ptr<Node> &ptr) {
	std::unique_ptr chd = std::move(prt->left);
	prt->left = std::move(chd->right);
	prt->height = 1 + std::max(Height(prt->left.get()), Height(prt->right.get()));
	chd->right = std::move(prt);
	chd->height = 1 + std::max(Height(chd->left.get()), Height(chd->right.get()));
	prt = std::move(chd);
}
```
![[Pasted image 20220426230145.png]]
### Left Rotation
```cpp
template <typename T>
void AVL::RotateLeft(std::unique_ptr &prt) {
	std::unique_ptr chd = std::move(prt->right);
	prt->right = std::move(chd->left);
	prt->height = 1 + std::max(Height(prt->right.get()), Height(prt->left.get()));
	chd->left = std::move(prt);
	chd->height = 1 + std::max(Height(chd->right.get()), Height(chd->left.get()));
	prt = std::move(chd);
}
```
![[Pasted image 20220426230309.png]]
### Insert and Remove
- Same body as BST
- Additional **retracing step** on the way back from the recursion 
```cpp
template <typename T>
void AVL<T>::Insert(std::unique_ptr<Node> &n, const T &key) {
	if (!n)
		n = std::unique_ptr(new Node{key});
	else if (key < n->key)
		Insert(n->left, key);
	
	Retrace(n);
}
...
	
template <typename T>
void AVL<T>::Remove(std::unique_ptr<Node> &n, const T &key) {
	//key not found
	if (!n) return;
	
	if (key < n->key) {
		Remove(n->left, key);
	} else if (key > n->key) {
		
	Retrace(n);
}
```

### Retracing
```cpp
template <typename T>
void AVL<T>::Retrace(std::unique_ptr<Node> &n) {
	if (!n) return;
	
	if (Height(n->left.get()) - Height(n->right.get()) > 1) {
		// Tree is left heavy: need rebalancing
		if (Height(n->left->left.get()) < Height(n->left->right.get()))
			// Left subtree is right heavy: need double rotation
			RotateLeft(n->left);
		RotateRight(n);
	} else if (Height(n->right.get()) - Height(n->left.get()) > 1) {
		// Tree is right heavy: need rebalancing
		if (Height(n->right->right.get()) < Height(n->right->left.get()))
			// Right subtree is left heavy: need double rotation
			RotateRight(n->right);
		RotateLeft(n);
	}
	// Adjust node's height
	n->height = 1 + std::max(Height(n->left.get()), Height(n->right.get()));
}

```
### Testing (1): insertion of ordered values
```cpp
std::vector keys{2, 18, 42, 43, 51, 54, 74, 93, 99};
AVL<int> avl;
for (auto i : keys) {
	avl.Insert(i);
	avl.Print();
}

```
Result:
```
2 (1)
2 (1) 18 (2)
2 (2) 18 (1) 42 (2)
2 (2) 18 (1) 42 (2) 43 (3)
2 (2) 18 (1) 42 (3) 43 (2) 51 (3)
2 (3) 18 (2) 42 (3) 43 (1) 51 (2) 54 (3)
2 (3) 18 (2) 42 (3) 43 (1) 51 (3) 54 (2) 74 (3)
2 (3) 18 (2) 42 (3) 43 (1) 51 (3) 54 (2) 74 (3) 93 (4)
2 (3) 18 (2) 42 (3) 43 (1) 51 (3) 54 (2) 74 (4) 93 (3) 99 (4)
```

### Testing (2): 100 random pairs of insertion/deletion
```cpp
std::mt19937 rng(0);
// Create uniform distribution of numbers
std::uniform_int_distribution distr(0, 99);

// Insert and delete 100 times
for (int i = 0; i < 100 ; i++) {
	// Insert random key that is not already in AVL
	int rval;
	do {
		rval = distr(rng);
	} while (avl.Contains(rval));
	avl.Insert(rval);
	keys.push_back(rval);
	
	// Remove existing random key from the AVL
	std::shuffle(keys.begin(), keys.end(), rng);
	avl.Remove(keys.back());
	keys.pop_back();
}
// AVL should still be balanced
avl.Print();
```
Result:
```
12 (3) 24 (4) 28 (2) 39 (3) 41 (4) 48 (1) 77 (3) 78 (2) 94 (3)
```

### Conclusion
Average and worst-case running times
![[Pasted image 20220426232226.png]]
#### Characteristics
- Very efficient for lookups because well-balanced
	- At most, height of $1.44 log_2(N+2) - 1.328 ≈ 1.44 logN$
- Rigid balancing which can be potentially slow down insertions and removals


## References
1.

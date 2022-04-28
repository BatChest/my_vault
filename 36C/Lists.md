# Lists
Created: 2022-04-11 17:45

### Abstract Data Types
#### Terminology
###### Type 
- Collection of values 
- boolean (true/false), int (-1, 0, 1, ...), float, etc.
	- Simple type: no subparts
	- Aggregate/composite type: record containing fields (struct { ... })

###### Data Type
- Type and collection of operations to manipulate the type
```ad-example
+ - * /, == != < >, etc
```
###### Abstract Data Type
- specification of data type, independent implementation
- Like lists, stack, queue, dictionary, sets and more

###### Data Structure
- Implementation of an ADT
- Like arrays, singly linked list, doubly linked list, hash table, trees

### List ADT
#### Definition
- Ordered collection of items of some type T

##### Operations
- Typical set of operations (API)
```cpp
// return number of items in list
size_t Size();
// Return itme at postion @pos
const T& Get(const size_t pos);
// Return position of first occurence of @item (-1 if not found)
int Find(const T &item);
// Remove item at position @pos
void Remove(const size_t pos);
// Insert @item at position @pos
void Insert(const T &item, const size_t pos);
```
##### Typical Implementations
- Arrays(fixed or dynamic) ![[Pasted image 20220411180742.png|150]]
- Linked list(singly or doubly linked) ![[Pasted image 20220411180806.png|150]]
- Even trees ![[Pasted image 20220411180820.png|150]]

```cpp
ListFixedArray<int> 1;
```
![[Pasted image 20220411181250.png|350]]

```cpp
l.Insert(23, 0);
```
![[Pasted image 20220411181316.png|350]]

```cpp
l.insert(42, 1.Size());
```
![[Pasted image 20220411181331.png|350]]

```cpp
l.Insert(99, 0);
```
![[Pasted image 20220411181343.png|350]]

```cpp
l.Remove(1);
```
![[Pasted image 20220411181354.png|350]]

#### Fixed Array Implementation
###### Data Structure
```cpp
template <typename T>
class ListFixedArray {
 private:
 // Fixed capacity of 3 items
 static constexpr size_t capacity = 3;
 std::array<T, capacity> items;
 size_t cur_size = 0;
};
```
- static to make capacity exists without instantiating and constexpr to make it available to compiler
- std::array is equivalent to a C-style array (T items [ capacity ])
- Member variables already initialized

###### Contructor/Destructor
```cpp
public:
ListFixedArray() = default;
~ListFixedArray() = default;
```
- default to have the compiler generate the corresponding constructor or destructor:  
	- No initialized
	- Empty compound statement

###### LIST API

```cpp
size_t Size() {
	return cur_size;
}
```

```cpp
const T& Get(const size_t pos) {
	if(pos >= cur_size)
		throw std::out_of_range("Position out of range!");
	return items[pos];
}
```

```cpp
int Find(const T &item) {  
	for (size_t i = 0; i < cur_size; i++)  
		if (items[i] == item)  
			return i;  
		return -1;  
}
```

```cpp
void Remove(const size_t pos) {
	if (pos >= cur_size)
		throw std::out_of_range("Position out of range");
	for (auto i = pos + i; i < cur_size; i++)
		items[i-1] = items[i];
	cur_size--;
}
```
![[Pasted image 20220426182112.png|400]]

```cpp
void Insert(const T &item, const size_t pos) {
	if (pos > cur_size)
		throw std::out_of_range("Position out of range!");
	if (cur_size == capacity)
		throw std::overflow_error("List full!");
	
	if (pos != cur_size) {
	//Move existing item(s)
		auto i = cur_size - 1;
		do {
			items[i + 1] = items[i];
		} while (i-- != pos);
	}
	items[pos] = item;
	cur_size++;
}
```
![[Pasted image 20220426182519.png|400]]
###### Conclusion
- Pros 
	- Implementation is straight forward
	- Little to no waste of memory space if number of items matches capacity of list on average

- Cons
	- Waste of space if list mostly empty 
	- Really just an array, not an actual list 
		- Insertion and removal operations are limited

### Dynamic Array Implementation
#### Option 1
- Insert(): increase size of array by 1
- Remove(): decrease size of array by 1.

#### Problem
Resizing the array on each operation is too expensive!
- Need to copy all items to new array, for each operation 
- To add first $n$ items, complexity would be $O(n^2)$

#### Option 2
- Resizing must be a *rare* event
- But without wasting to much extra memory space...

#### Resizable Data Structure
```cpp
template <typename T>
class ListDynamicArray {
	private:
		//Inital capactiy of 3 items
		size_t capacity = 3;
		std::unique_ptr<T[]> items;
		size_t cur_size = 0;
	...
		
	public:
		ListDynamicArray() : items(std::unique_ptr<T[]>(new T[capacity])) {}
	~ListDynamicArray() = default;
};
```
- Capacity is no longer a constant 
- Smart pointer for array of items
	- Ensures list is sole owner of the array
	- Auto-destuction when list disappears

```cpp
// Resize array according to new capacity  
void Resize(size_t new_cap) {  
	assert(new_cap && new_cap >= cur_size);  
	std::unique_ptr<T[]> new_items(new T[new_cap]);  
	std::move(items.get(),  
		std::next(items.get(), cur_size),  
		new_items.get());  
	std::swap(items, new_items);  
	capacity = new_cap;  
}
```
- assert() for checking internal invariants
- Efficient data transfer from one array to another win std::move()
- Efficient exchange of values between smart pointers with std::swap()

#### Growing Strategy
- If array is full, create a new of twice the size and copy items
```cpp
void Insert(const T &item, const size_t pos) {  
...  
	// Grow by 2 when reaching max capacity  
	if (cur_size == capacity)  
		Resize(2 * capacity);  
...  
}
```

#### Growing Strategy Complexity Analysis
Example: insert $(n + 1)$ items at the end of the list

##### Usual Big-O analysis
For  one insertion:
- Best Case(array still has room): $O(1)$
- Worst case (array has to be expanded first): $O(N)$
- Average case (?): ?

How can we be more precise?
##### Amortized analysis
- $n$ operations take constant time: $O(1)$
- Last operation take linear time: $O(n)$
- Total time: $T(n+1) = nO(1)+O(n)$
- Amortized time complexity for one operation: $\frac{nO(1)+O(n)}{n+1} = O(1)$

#### Shrinking Strategy
- Halve the array when array is one-half full?
Problem
Too expensive for (possible) worst-case scenario:
- Push-pop-push-...sequence when array is full
- Each operation takes linear time
![[Pasted image 20220426190316.png]]

- Halve the array when array is one-quarter full
```cpp
void Remove(const size_t pos)
{
	//Shrink by 2 when reaching 25% of capacity
	if (cur_size <= capacity / 4)
		Resize(Capacity/2);
}
```
#### Conclusion 
##### Pros
- Full implementation of the List ADT
- Efficient indexing: $O(1)$
- Efficient insert/remove at end: $O(1)$ amortized

##### Cons
- Implementation is more complex
- Some waste of space
	- Array is always between 25% and 100% full
- Inefficient insert/remove at beginning/middle: $O(N)$

### Singly Linked List Implementation
```cpp
ListSinglyLinked<int> l; 
```
![[Pasted image 20220426190745.png]]

```cpp
l.Insert(23, 0);
```
![[Pasted image 20220426190808.png]]

```cpp
l.Insert(42, l.Size());
```
![[Pasted image 20220426190824.png]]

```cpp
l.Insert(99, 0);
```
![[Pasted image 20220426190842.png]]

```cpp
l.Remove(1);
```
![[Pasted image 20220426190859.png]]

#### Data Structure
```cpp
template <typename T>  
class ListSinglyLinked {  
	private:  
		struct Node {  
			T item;  
			std::unique_ptr<Node> next;  
	};  
	std::unique_ptr<Node> head = nullptr;  
	size_t cur_size = 0;  
...  
	public:  
		ListSinglyLinked() = default;  
...  
		~ListSinglyLinked() = default;  
...  
};

```
- Internal node structure: data and next pointer
- Use of smart pointers for ensuring sole ownership

```cpp
	Node* GetNode(size_t pos) {  
		assert(pos < cur_size);  
		Node *n = head.get();  
		while (pos--)  
			n = n->next.get();  
		return n;  
}
```
- Internal get() method for access to any node on linked list
	- Use of regular pointer because of list traversal is not about ownership

#### LIST API
```cpp
size_t Size() {  
	return cur_size;  
}

```

```cpp
const T& Get(const size_t pos) {  
	if (pos >= cur_size)  
		throw std::out_of_range("Position out of range!");  
	auto n = GetNode(pos);  
	return n->item;  
}
```

```cpp
int Find(const T &item) {  
	int i = 0;  
	for (auto n = head.get(); n; n = n->next.get(), i++)  
		if (n->item == item)  
			return i;  
	return -1;  
}
```

```cpp
void Remove(const size_t pos) {  
	if (pos >= cur_size)  
		throw std::out_of_range("Position out of range!");  
	if (!pos) {  
		// Remove from top of list  
		auto n = std::move(head);  
		head = std::move(n->next);  
		} else {  
		// Remove after existing item(s)  
		auto prev = GetNode(pos - 1);  
		auto n = std::move(prev->next);  
		prev->next = std::move(n->next);  
	}  
	cur_size--;  
}
```

- Transfer node's ownership to local smart pointer variable n with std::move()
	- Automatically destroyed when goes out of scope
- Because singly linked list, need to get hold of previous node to remove specified node (not the case with doubly linked lists)
![[Pasted image 20220426191810.png]]

```cpp
void Insert(const T &item, const size_t pos) {  
	if (pos > cur_size)  
		throw std::out_of_range("Position out of range!");  
	auto n = std::unique_ptr<Node>(new Node);  
	n->item = item;  
	if (pos == 0) {  
		// Insert in front  
		n->next = std::move(head);  
		head = std::move(n);  
	} else {  
		// Insert after existing item(s)  
		auto prev = GetNode(pos - 1);  
		n->next = std::move(prev->next);  
		prev->next = std::move(n);  
	}  
	cur_size++;  
}
```
- Usual singly linked list insertion
	- Change head pointer for insertion at beginning
	- Change previous node for insertion at middle or end

#### Conclusion
##### Pros
- Fairly simple implementation
- Insert/remove at beginning: $O(1)$

##### Cons
- Inefficient indexing: $O(N)$
- Inefficient insert/remove at middle/end: $O(N)$
- Only forward traversal 
	- E.g., what would be the complexity of potential API function r_find()?

### Doubly Linked List Implementation
#### Pointer to previous node
- Efficient reverse traversal
- Easier removal of a node
![[Pasted image 20220426200250.png]]

#### Optimization: pointer to tail
- Efficient insert/remove at end
![[Pasted image 20220426200328.png]]
#### Conclusion
##### Pros
- Efficient insert/remove at end: $O(1)$
- Possibility of reverse traversal if required by API

##### Cons
- Slightly more complex than singly linked list for insertion

### Comparison of Data Structures
![[Pasted image 20220426200432.png]]

### Standard C++ Containers
The C++ Standard Library defines two popular implementations of the list ADT (a.k.a.  
sequence containers):
- std::vector
	- Internally based on a dynamic array
	- "Unless you have a solid reason not to, use a vector" (Stroustrup,  
		2013)
- std::list
	- Internally based on a doubly linked list

And two other less popular implementations:
- std::forward_list
	- Internally based on a singly linked list
	- (Good for empty and very short sequences)
- std::deque
	- Double-ended queue
	- Internally based on an array of fixed-size arrays
	- (Good at growing in both directions)
#### Vector
```cpp
#include <iostream>  
#include <vector>  
int main() {  
	std::vector<int> v = {7, 5, 16, 8};  
	// Direct [] access to values  
	v[1] = 10;  
	// Insert at beginning and middle  
	v.insert(v.begin(), 42);  
	v.insert(v.begin() + v.size() / 2, 23);  
	// Insert at end  
	v.push_back(25);  
	v.push_back(13);  
	
	// Remove last element  
	v.pop_back();  
	// Iterate and print values  
	for (auto n : v)  
		std::cout << n << std::endl;  
	return 0;  
}

```
Execution:
```
42  
7  
23  
10  
16  
8  
25
```

#### List
```cpp
#include <algorithm>  
#include <iostream>  
#include <list>  
int main() {  
	std::list<int> l = { 7, 5, 16, 8 };  
	// Add an integer to the front of the list  
	l.push_front(25);  
	// Add an integer to the back of the list  
	l.push_back(13);  
	// Insert an integer before 16 by searching  
	auto it = std::find(l.begin(), l.end(), 16);  
	if (it != l.end()) {  
		l.insert(it, 42);  
	}  
	// Iterate and print values of the list  
	for (auto n : l) {  
		std::cout << n << std::endl;  
	}  
}
```
Execution:
```
25  
7  
5  
42  
16  
8  
13
```

#### Vector vs List
- Insertion of random integers in collection 
- Keep collection sorted
	- Find proper location
	- Insert new integer
- Based on complexity analysis, which  container should perform better?

##### Explanation
- std::vector's internal array is stored contiguously in memory
	- Much of the array can be cached in processor resulting in very fast access
- std::list's nodes are not contiguous in memory
	- Causes lots of physical transfer between processor and RAM memory
##### Conclusion
- std::vector is generally faster and more efficient than std::list (apart when dealing with  
	big items *)

## References
1.

# Stack and Queues
Created: 2022-04-26 20:12

## Stack ADT
### Definition 
Subset of a list with two main operations
- **Push**: adds an item to the list
- ** Pop**: removes the most recently added item from the list
![[Pasted image 20220426201405.png]]
- Also sometimes called **LIFO** (Last In, First Out)
### Typical API
```cpp
// Return number of items in stack  
size_t Size();  
// Return top of stack  
T& Top();  
// Remove top of stack  
void Pop();  
// Push item to top of stack  
void Push(const T &item);
```
#### Typical Implementations
- Array (vector)
	- Push and pop to/from end of array $O(1)$ *amortized* ![[Pasted image 20220426201547.png]]
- (Singly) linked list
	- Push and pop to/from beginning of list $O(1)$ ![[Pasted image 20220426201617.png]]

### Array Implementation
```cpp
template <typename T>  
class Stack {  
...  
	private:  
		std::vector<T> items;  
};  
template <typename T>  
size_t Stack<T>::Size() {  
	return items.size();  
}
```

```cpp
template <typename T>  
T& Stack<T>::Top() {  
	if (!items.size())  
		throw std::underflow_error("Empty stack!");  
	return items.back();  
}  

template <typename T>  
void Stack<T>::Pop() {  
	if (!items.size())  
		throw std::underflow_error("Empty stack!");  
	items.pop_back();  
}  
template <typename T>  
void Stack<T>::Push(const T &item) {  
	items.push_back(item);  
}
```
- Entirely based on std::vector
	- Wrappers to subset of methods
	- With a bit of error management

### Linked List Implementation
```cpp
template <typename T>  
class Stack {  
...  
	private:  
		size_t cur_size = 0;  
		std::forward_list<T> items;  
};  

template <typename T>  
size_t Stack<T>::Size() {  
	return cur_size;  
}
```

```cpp
template <typename T>  
T& Stack<T>::Top() {  
	if (!cur_size)  
		throw std::underflow_error("Empty stack!");  
	return items.front();  
}  
template <typename T>  
void Stack<T>::Pop() {  
	if (!cur_size)  
		throw std::underflow_error("Empty stack!");  
	items.pop_front();  
	cur_size--;  
}  
template <typename T>  
void Stack<T>::Push(const T &item) {  
	items.push_front(item);  
	cur_size++;  
}
```
- Entirely based on std::forward_list
	- With current size info
	- With a bit of error management

### Some Application Examples
#### Balanced Symbol Checking 
- Compiler checks that every right brace, bracket and parenthesis correspond to its left  
counterpart.
```cpp
if (array[0) { std::cout << "Hurray!" << std::endl; }  
		  ^  
		  error: expected ']' before ')' token
```
- Algorithm (in pseudocode) using a stack:
```cpp
create empty stack  
do  
	get next token in file  
	if token is opening symbol  
		push on stack  
	else if token is closing symbol  
		pop from stack  
		if popped symbol is not the corresponding opening symbol  
			report error!  
while not end of file  
if stack not empty  
	report error!
```
### Postfix Expression
- Infix expressions can be interpreted differently, according to which precedence is given to operator. Ex: how to calculate 4 + 5 + 6 * 2?
	- Is it (4 + 5 + 6) * 2 = 30 or 4 + 5 + (6 * 2) = 21?
	- The latter is the scientific answer, as multiply has higher precedence
- With a postfix notation (a.k.a. Reverse Polish Notation), the order of evaluation becomes explicit and does not require parentheses
	- 4 5 + 6 2 * +
	- Used by HP in all their calculators in the 70s and 80s
	- Can easily be computed using a stack!
```
create empty stack  
do  
	if token is number then  
		push to stack  
	else if token is operator then  
		pop two numbers from stack  
		perform operation  
		push result to stack  
while there are still tokens  
pop final result from stack
```

### Function Calls
- Inherent structure under most function calling conventions
- Call stack:
	- Arguments to a function are pushed into new stackframe
	- Stackframe also holds local variables (e.g. in C)
	- Popped when function returns
	- Supports nested and recursive function calls
```cpp
int f(int n) {  
	if (n == 0)  
		return 1  
	else  
		return n * f(n - 1);  
}  
void g(void) {  
	int a = 4;  
	int b = f(a);  
}
```
![[Pasted image 20220426202800.png]]

## The Queue ADT
### Definition
Also a subset of a list with two main operations:
- **Enqueue**: adds an item to the list
- **Dequeue**: removes the least recently added item from the list
![[Pasted image 20220426202948.png]]
- Also sometimes called FIFO (First In, First Out)
### Typical API
```cpp
// Return number of items in queue  
size_t Size();  
// Return front of queue  
T& Front();  
// Remove front of queue  
void Pop();  
// Push item to back of queue  
void Push(const T &item);
```
#### Typical Implementations
- (Doubly) linked list
	- Push to end and pop from beginning of list $O(1)$ 
- Circular Array ![[Pasted image 20220426203121.png]]
### Linked List Implementation 
```cpp
template <typename T>  
class Queue {  
...  
	private:  
		std::list<T> items;  
};  
template <typename T>  
size_t Queue<T>::Size() {  
	return items.size();  
}
```

```cpp
template <typename T>  
T& Queue<T>::Front() {  
	if (!items.size())  
		throw std::underflow_error("Empty queue!");  
	return items.front();  
}  
template <typename T>  
void Queue<T>::Pop() {  
	if (!items.size())  
		throw std::underflow_error("Empty queue!");  
	items.pop_front();  
}  
template <typename T>  
void Queue<T>::Push(const T &item) {  
	items.push_back(item);  
}
```
- Entirely based on std::list
	- Wrappers to subset of methods
	- With a bit of error management
### Application Examples
- Some algorithms related to graphs
![[Pasted image 20220426203400.png]]
- Queue of jobs for printers
![[Pasted image 20220426203408.png]]
- Pipes (inter-process communication)
![[Pasted image 20220426203415.png]]
- I/O requests scheduling (e.g. disk, network)
![[Pasted image 20220426203422.png]]

### Standard C++ Containers
The C++ Standard Library defines the implementations of a stack ADT and a queue ADT.
Both are only adaptor containers as they are only wrappers to underlying sequence  
containers:
- std::stack
	- Can be implemented with std::dequeue (default), std::list and std::vector
```cpp
// By default, will be based on a deque  
std::stack<int> st_dq;  

// But can also specify another container  
std::stack<int, std::list<int>> st_lst;
```
- std::queue
	- Can be implemented with std::dequeue (default) and std::list
#### Stack
```cpp
void check_balance(std::string &str) {  
	static const std::string symbols[] = { "({[", ")}]" };  
	std::stack<char> balance;  
	for (auto c : str) {  
		// 1. Check if c is an opening symbol  
		if (symbols[0].find(c) != std::string::npos) {  
			balance.push(c);  
			continue;  
		}  
		// 2. Check if c is an closing symbol  
		auto pos = symbols[1].find(c);  
		if (pos == std::string::npos)  
			continue; // skip if not  
		// 3. Check proper symbol matching  
		if (!balance.empty() && balance.top() == symbols[0][pos]) {  
			balance.pop();  
		} else {  
			std::cerr << "Unbalanced string!" << std::endl;  
			return;  
		}  
	}  
	if (!balance.empty())  
		std::cerr << "Unbalanced string!" << std::endl;  
}
```
Execution
```
$ "[(){}]"  
$ ")"  
Unbalanced string!  
$ "[(){]"  
Unbalanced string!
```


## References
1.

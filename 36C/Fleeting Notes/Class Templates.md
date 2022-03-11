Created: 2022-03-05 19:57
Status: #idea
Tags: [[C++]]
# Class Templates

What's the point of this?
Use class implementation that is same for all classes and the data type is the only difference
Using Class Templates will let us reuse parts of our code which would make it easier to create new class with different data types;

```ad-example
![[Screenshots/Pasted image 20220305200345.png]]
The two functions are nearly identical but one take in integer data type while the other take in character data types
This creates reusability within our code
```

```ad-info
~~~c++
#include <iostream>
using namespace std;

template <typename T>
class Weight{
	private:
		T kg;
	
	public:
		void setData(T x)
		{
			kg = x;
		}
		T getData()
		{
			return kg;
		}
};

int main() {
	
	Weight <int>obj1;
	obj1.setData(5);
	cout << "Value is: " << obj1.getData() << endl;
	
	Weight <double>obj2;
	obj2.setData(5.43353);
	cout << "Value is: " << obj2.getData() << endl;
	return 0;
}
~~~

When compiling and running our output should be 5 and 5.43353
This is just a basic of template classes and how we can reuse our code
```

# References
1. https://www.youtube.com/watch?v=CWj7lLY2GLA

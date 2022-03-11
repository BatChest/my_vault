Created: 2022-03-05 20:17
Status: #idea
Tags: [[C++]]
# Function Templates
Special functions that operate generic types

Allows users to create function templates whose functionality can be reused to different types and classes wihtout having to rewrite code

We are just passing data type as parameter

A base function that can be reused by different data types

```ad-example 
~~~c++
template <typename>
T add(T x, T y)
{}

int main ()
{
	add<int>(3,7);
	add<float>(3.3, 7.5);
	add<double>(3.55, 7.66);
}
We can add three different data types using the same function with the template and all we are changing is the data type we are taking in
```

```ad-example
~~~c++
#include <iostream>
using namespace std;

template<typename T>
T add(T x, T y)
{
	return(x+y);
}

int main(){
	cout << "Addition of 2 integers 3 and 4 is: " << add<int>(3,4) 
	<< endl;
	cout << "Addition of 2 float variables 3.4 and 4.2 is: " << 
	add<float>(3.4f,4.2f) << endl;
	cout << "Addition of 2 double variables 3.45 and 4.23 is: " << 
	add<double>(3.45,4.23) << endl;
	return 0;
}
~~~
We should be getting 7, 7.6 and 7.68 as our outputs.
The "T" is being used a placeholder so whenever we decide to use a data type on our function template we are then going to replace that "T" with whatever data type we want to use.
```

Now if we wanted to take in two data types for our functions then it would be as simple as:
```ad-example
~~~c++
template<typename T, typename U>
U add (T x, U y)
{
	return(x+y);
}

//when calling the function we would then have two data types being pass through

add<int,double>(3,3.5);
~~~
Our output should be 6.5 because we made "U" our data type for the function add and because double is taking the place as "U" then the function is going to be returning a double.
If we use "T" instead then we would then have 6 as our output since T is an int.

```

# References
1. https://www.youtube.com/watch?v=bP1ceQFbohM

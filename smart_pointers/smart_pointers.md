## Smart Pointers

A Smart Pointer is a wrapper class over a pointer with an operator like * and -> overloaded. The objects of the smart pointer class look like normal pointers. But, unlike Normal Pointers it can deallocate and free destroyed object memory.

Pointers in C and C++ languages are wild beasts. They are extremely powerful, and also they are  so dangerous, a little oversight may wreak havoc on your whole app. Every dynamically allocated object (`i.e. new T`) must be followed by a manual deallocation (`i.e. delete T`). Forget to do that and you will end up with a nice memory leak.

Moreover, dynamically allocated arrays (`i.e. new T[N]`) require to be deleted with a different operator (`i.e. delete[]`). This forces you to mentally keep track of what you have allocated, and call the right operator accordingly. Using the wrong form results in **undefined behavior**, something you really want to avoid at all costs when working in C++.


###### Example 
```cpp

#include <iostream>
using namespace std;
 
class Rectangle 
{
private:
    int length;
    int breadth;
};
 
void fun()
{
    // By taking a pointer p and dynamically creating object of class rectangle

    Rectangle* p = new Rectangle();
}
 
int main()
{
    // Infinite Loop
    while (1) 
    {
        fun();
    }

    return 0;
}

```
###### Description

*In function fun, it creates a pointer that is pointing to the Rectangle object. The object Rectangle contains two integers, length and breadth. When the function fun ends, p will be destroyed as it is a local variable. But, the memory it consumed won’t be deallocated because we forgot to use delete p; at the end of the function. That means the memory won’t be free to be used by other resources. But, we don’t need the variable anymore, but we need the memory.*

*In function main, fun is called in an infinite loop. That means it’ll keep creating p. It’ll allocate more and more memory but won’t free them as we didn’t deallocate it. The memory that’s wasted can’t be used again. Which is a memory leak. The entire heap memory may become useless for this reason.*


Another critical problem lies in **ownership**. A third-party function returns a pointer: is it dynamically-allocated data? If so, who is responsible for the cleanup? There is no way to infer such information by simply looking at the return.


### The Idea Behind Smart Pointers

**C++11** comes up with its own mechanism that’s Smart Pointer. Smart pointers were born to fix the annoyances mentioned above. They basically provide **automatic memory management**: when a smart pointer is no longer in use, that is when it goes out of scope, the memory it points to is deallocated automatically. Traditional pointers are now also known as raw pointers.

A **Smart Pointer is a wrapper class** over a pointer(`raw pointer`) with an operator like` *` and `->` overloaded. The objects of the smart pointer class look like normal pointers. But, unlike Normal Pointers it can deallocate and free destroyed object memory.

Smart pointers can be seen as a rudimentary form of garbage collection: a kind of automatic memory management where object are automatically deleted when are no longer in use by the program.

Bonus point: in case a third-party function returns a smart pointer, you can quickly deduce its type, what you can do with it and how the data lifetime is managed.

The idea is to take a class with a pointer, destructor and overloaded operators like * and ->. Since the destructor is automatically called when an object goes out of scope, the dynamically allocated memory would automatically be deleted (or reference count can be decremented). 

Consider the following simple SmartPtr class to understand smart pointers.

###### Example:

```cpp
#include <iostream>
using namespace std;

class SmartPtr 
{
	int* ptr; // Actual pointer
public:
	// Constructor: use of explicit keyword
	explicit SmartPtr(int* p = NULL) 
	{ 
		ptr = p; 
	}

	// Destructor
	~SmartPtr() 
	{ 
		delete (ptr); 
	}

	// Overloading dereferencing operator
	int& operator*() 
	{
		return *ptr; 
	}
};

int main()
{
	SmartPtr ptr(new int());
	*ptr = 20;
	cout << *ptr;

	// We don't need to call delete ptr: when the object ptr goes out of scope, 
	// the destructor for it is automatically called and destructor does delete ptr.

	return 0;
}
```

###### Output: 
```sh
20 
```

Above code is only for int type data. If we want to create Smart Pointer for class type object then there’s a solution, **Template**. In the code below as you can see T can be of any type of data.

###### Example 
```cpp
#include <iostream>
using namespace std;

// A generic smart pointer class
template <class T>
class SmartPtr 
{
	T* ptr; // Actual pointer
public:
	// Constructor
	explicit SmartPtr(T* p = NULL) 
	{ 
		ptr = p; 
	}

	// Destructor
	~SmartPtr() 
	{ 
		delete (ptr); 
	}

	// Overloading dereferencing operator
	T& operator*() 
	{ 
		return *ptr; 
	}

	// Overloading arrow operator so that members of T can be accessed
	// like a pointer (useful if T represents a class or struct or union type)
	T* operator->() { return ptr; }
};

int main()
{
	SmartPtr<int> ptr(new int());
	*ptr = 20;
	cout << *ptr;
	return 0;
}
```
###### Output:
```sh
20 
```

### Types of Smart Pointers
**C++11** has introduced three types of smart pointers, all of them defined in the `<memory>` header from the Standard Library:

* **[Unique Pointer](./unique_ptr.html)** - a smart pointer that owns a dynamically allocated resource;

* **[Shared Pointer](./shared_ptr.html)** - a smart pointer that owns a shared dynamically allocated resource. Several `std::shared_ptr` may own the same resource and an internal counter keeps track of them;

* **[Weak Pointer](./weak_ptr.html)** - like a `std::shared_ptr`, but it doesn't increment the counter.

* **[Auto Pointer](#)** - In C++11 it is deprecated so forget about it.

Things look confusing right now, especially which type of smart pointer one should use. Let's dig deeper!


---

<style>
.my-ft-link:link, .my-ft-link:visited {
  background-color: white;
  color: black;
  border: 2px solid green;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

.my-ft-link:hover, .my-ft-link:active {
  background-color: green;
  color: white;
}
  
.my-footer {
  text-align: center;
}

.my-footer1 {
  text-align: left;
  display:inline;
}

.my-footer2 {
  text-align: right;
  display:inline;
}
</style>

<div class="my-footer">
  <div class="my-footer1">
    <a href="https://brightkoder.github.io/" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="./unique_ptr.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---

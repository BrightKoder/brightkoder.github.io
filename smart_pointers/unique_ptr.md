### Unique Pointer

`std::unique_ptr` was developed in **C++11** as a replacement for `std::auto_ptr`.

A `std::unique_ptr` owns of the object it points to and no other smart pointers can point to it. When the `std::unique_ptr` goes out of scope, the object is deleted. When this object is destructed then in its destructor it deletes the associated raw pointer.

`std::unique_ptr` has its `->` and `*` operator overloaded, so it can be used similar to normal pointer.

There are two versions of std::unique_ptr:

1. Manages a single object (e.g. allocated with new)
2. Manages a dynamically-allocated array of objects (e.g. allocated with new[])

This is defined in include file
```cpp
#include <memory>
```

#### How to construct:

A `std::unique_ptr` is created like this:

```cpp
std::unique_ptr<Type> p(new Type);
```

Example:
```cpp
std::unique_ptr<int>    p1(new int);
std::unique_ptr<int[]>  p2(new int[50]);
std::unique_ptr<Object> p3(new Object("Lamp"));
```
###### Example:
```cpp
#include <iostream>
#include <memory>
struct Task
{
    int mId;
    Task(int id ) :mId(id)
    {
        std::cout<<"Task::Constructor"<<std::endl;
    }
    ~Task()
    {
        std::cout<<"Task::Destructor"<<std::endl;
    }
};
int main()
{
    // Create a unique_ptr object through raw pointer
    std::unique_ptr<Task> taskPtr(new Task(23));
    //Access the element through unique_ptr
    int id = taskPtr->mId;
    std::cout<<id<<std::endl;
    return 0;
}
```

###### Output:
```sh
Task::Constructor 
23 
Task::Destructor 
```
We can not create a `std::unique_ptr<Type>` object through assignment, otherwise it will cause compile error
```cpp
std::unique_ptr<Task> taskPtr2 = new Task(); // Compile Error
```

It is also possible to construct `std::unique_ptr`s with the help of the special function `std::make_unique`, like this:
```cpp
std::unique_ptr<Type> p = std::make_unique<Type>(...size or parameters...);
```
C++14 comes with an additional function named `std::make_unique()`. This templated function constructs an object of the template type and initializes it with the arguments passed into the function.

Use of `std::make_unique()` is optional, but is recommended over creating `std::unique_ptr` yourself. This is because code using `std::make_unique` is simpler, and it also requires less typing (when used with automatic type deduction). Furthermore it resolves an exception safety issue that can result from C++ leaving the order of evaluation for function arguments unspecified.

Example:
```cpp
std::unique_ptr<int>    p1 = std::make_unique<int>();
std::unique_ptr<int[]>  p2 = std::make_unique<int[]>(50);
std::unique_ptr<Object> p3 = std::make_unique<Object>("Lamp");
```
If you can, always prefer to allocate objects using `std::make_unique`.

#### Ownerships with Unique pointers

It explicitly prevents copying of its contained pointer as would happen with normal assignment i.e. it allows exactly one owner of the underlying pointer.

So, when using unique_ptr there can only be at most one unique_ptr at any one resource and when that unique_ptr is destroyed, the resource is automatically claimed. 

Also, since there can only be one unique_ptr to any resource, so any attempt to make a copy of unique_ptr will cause a compile-time error.

```cpp
unique_ptr<A> ptr1 (new A);

// Error: can't copy unique_ptr
unique_ptr<A> ptr2 = ptr1;

```


But, `unique_ptr` can be moved using the new move semantics i.e. using `std::move()` function to transfer ownership of the contained pointer to another `unique_ptr`.


```cpp

// Works, resource now stored in ptr2
unique_ptr<A> ptr2 = move(ptr1); 

```
So, it’s best to use unique_ptr when we want a single pointer to an object that will be reclaimed when that single pointer is destroyed.

###### Example

```cpp
// C++ program to illustrate the use of unique_ptr
#include <iostream>
#include <memory>
using namespace std;

class A {
public:
	void show()
	{
		cout << "A::show()" << endl;
	}
};

int main()
{
	unique_ptr<A> p1(new A);
	p1->show();

	// returns the memory address of p1
	cout << p1.get() << endl;

	// transfers ownership to p2
	unique_ptr<A> p2 = move(p1);
	p2->show();
	cout << p1.get() << endl;
	cout << p2.get() << endl;

	// transfers ownership to p3
	unique_ptr<A> p3 = move(p2);
	p3->show();
	cout << p1.get() << endl;
	cout << p2.get() << endl;
	cout << p3.get() << endl;

	return 0;
}
```
###### Output
```sh
A::show()
0x1c4ac20
A::show()
0          // NULL
0x1c4ac20
A::show()
0          // NULL
0          // NULL
0x1c4ac20
```
#### Returning Unique Pointer from a function

`std::unique_ptr`can be safely returned from a function by value:

smart pointers are powered by move semantics: the dynamically-allocated resource they hold is moved around, not wastefully copied;

Modern compilers play the **Return Value Optimization (RVO)** trick. They are able to detect that you are returning an object by value, and they apply a sort of return shortcut to avoid useless copies. 

Starting from C++17, this is guaranteed by the standard. So even the smart pointer itself will be optimized out;

###### Example

```cpp
#include <iostream>
#include <memory> // for std::unique_ptr

class Resource {};

std::unique_ptr<Resource> createResource()
{
	std::cout << "Inside createResource()"
    return std::make_unique<Resource>();
}

int main()
{
	std::cout << "Inside main()"
    auto ptr = createResource();

    std::cout << ptr.get() << std::endl;

    // do whatever

    return 0;
}

```

###### Output

```sh
Inside createResource()
0x1c4ac20 
Inside main()
```

In the above code, `createResource()` returns a `std::unique_ptr` by value. If this value is not assigned to anything, the temporary return value will go out of scope and the Resource will be cleaned up.

If it is assigned (as shown in `main()`), in C++14 or earlier, move semantics will be employed to transfer the Resource from the return value to the object assigned to (in the above example, `ptr`), and in C++17 or newer, the return will be elided (see [Copy Elision technique](https://en.cppreference.com/w/cpp/language/copy_elision)). 

This makes returning a resource by `std::unique_ptr` much safer than returning raw pointers!

#### Passing Unique Pointer to a function
If you want the function to take ownership of the contents of the pointer, pass the std::unique_ptr by value. Note that because copy semantics have been disabled, you’ll need to use std::move to actually pass the variable in.

###### Example:

```cpp
#include <iostream>
#include <memory> // for std::unique_ptr
#include <utility> // for std::move

class Resource
{
public:
	Resource() { std::cout << "Resource acquired\n"; }
	~Resource() { std::cout << "Resource destroyed\n"; }
	friend std::ostream& operator<<(std::ostream& out, const Resource &res)
	{
		out << "I am a resource";
		return out;
	}
};

void takeOwnership(std::unique_ptr<Resource> res)
{
     if (res)
          std::cout << *res << '\n';
} // the Resource is destroyed here

int main()
{
    auto ptr{ std::make_unique<Resource>() };

//    takeOwnership(ptr); // This doesn't work, need to use move semantics
    takeOwnership(std::move(ptr)); // ok: use move semantics

    std::cout << "Ending program\n";

    return 0;
}

```
###### Output
```sh
Resource acquired
I am a resource
Resource destroyed
Ending program
```

Note that in this case, ownership of the Resource was transferred to `takeOwnership()`, so the Resource was destroyed at the end of `takeOwnership()` rather than the end of `main()`.

However, most of the time, you won’t want the function to take ownership of the resource. Although you can pass a `std::unique_ptr` by **reference** (which will allow the function to use the object without assuming ownership), you should only do so when the called function might alter or change the object being managed.

Instead, it’s better to just pass the resource itself (by pointer or reference, depending on whether null is a valid argument). This allows the function to remain agnostic of how the caller is managing its resources. 

To get a raw resource pointer from a `std::unique_ptr`, you can use the `get()` member function:

###### Example
```cpp
#include <memory> // for std::unique_ptr
#include <iostream>

class Resource
{
public:
	Resource() { std::cout << "Resource acquired\n"; }
	~Resource() { std::cout << "Resource destroyed\n"; }

	friend std::ostream& operator<<(std::ostream& out, const Resource &res)
	{
		out << "I am a resource";
		return out;
	}
};

// The function only uses the resource, so we'll accept a pointer to the resource, not a reference to the whole std::unique_ptr<Resource>
void useResource(Resource* res)
{
	if (res)
		std::cout << *res << '\n';
	else
		std::cout << "No resource\n";
}

int main()
{
	auto ptr{ std::make_unique<Resource>() };

	useResource(ptr.get()); // note: get() used here to get a pointer to the Resource

	std::cout << "Ending program\n";

	return 0;
} // The Resource is destroyed here
```

###### Output
```sh
Resource acquired
I am a resource
Ending program
Resource destroyed
```

#### Unique Pointer member functions

##### 1. std::unique_ptr::get()

###### Syntax
```cpp
Type *ptr = unique_ptr.get(void);
```

Returns a pointer to the **managed object**, or a **null pointer**. pointer is a member type, defined as the pointer type that points to the type of object managed.

The stored pointer points to the object managed by the `std::unique_ptr`, if any, or to nullptr if the `std::unique_ptr` is empty.

Notice that a call to this function does not make `std::unique_ptr` release ownership of the pointer (i.e., it is still responsible for deleting the managed data at some point). Therefore, the value returned by this function shall not be used to construct a new managed pointer.

###### Example

```cpp
// unique_ptr::get() vs unique_ptr::release()
#include <iostream>
#include <memory>

int main () {
                                           // foo   bar    p
                                           // ---   ---   ---
  std::unique_ptr<int> foo;                // null
  std::unique_ptr<int> bar;                // null  null
  int* p = nullptr;                        // null  null  null

  foo = std::unique_ptr<int>(new int(10)); // (10)  null  null
  bar = std::move(foo);                    // null  (10)  null
  p = bar.get();                           // null  (10)  (10)
  *p = 20;                                 // null  (20)  (20)
  p = nullptr;                             // null  (20)  null

  foo = std::unique_ptr<int>(new int(30)); // (30)  (20)  null
  p = foo.release();                       // null  (20)  (30)
  *p = 40;                                 // null  (20)  (40)

  std::cout << "foo: ";
  if (foo) std::cout << *foo << '\n'; else std::cout << "(null)\n";

  std::cout << "bar: ";
  if (bar) std::cout << *bar << '\n'; else std::cout << "(null)\n";

  std::cout << "p: ";
  if (p) std::cout << *p << '\n'; else std::cout << "(null)\n";
  std::cout << '\n';

  delete p;   // the program is now responsible of deleting the object pointed to by p
              // bar deletes its managed object automatically

  return 0;
}
```
###### Output

```sh
foo: (null) 
bar: 20 
p: 40 
```

##### 2. std::unique_ptr::release()
###### Syntax
```cpp
Type *ptr = unique_ptr.release(void);
```
Releases ownership of its **stored pointer**, by returning its value and replacing it with a **null pointer**. A pointer to the object managed by unique_ptr before the call. pointer is a member type, defined as the pointer type that points to the type of object managed.

This call does not destroy the managed object, but the `std::unique_ptr` object is released from the responsibility of deleting the object. Some other entity must take responsibility for deleting the object at some point.

###### Example 

```cpp
// unique_ptr::release() example
#include <iostream>
#include <memory>

int main () {
  std::unique_ptr<int> auto_pointer (new int);
  int * manual_pointer;

  *auto_pointer=10;

  manual_pointer = auto_pointer.release();
  // (auto_pointer is now empty)

  std::cout << "manual_pointer points to " << *manual_pointer << '\n';

  delete manual_pointer;

  return 0;
}

```
###### Output
```sh
manual_pointer points to 10 

```

##### 3. std::unique_ptr::reset()
###### Syntax
```cpp
void reset (pointer p = pointer()) noexcept;
```
Destroys the object currently managed by the unique_ptr (if any) and takes ownership of p.

If p is a null pointer (such as a default-initialized pointer), the `std::unique_ptr` becomes empty, managing no object after the call.

To release the ownership of the stored pointer without destroying it, use member function release instead.

###### Example

```cpp
// unique_ptr::reset() example
#include <iostream>
#include <memory>

class foo
{
	int idx;
public:
	foo(int id) { idx = id; }
	~foo() { std::cout << "~foo called\n"; }
};

int main () {
  std::unique_ptr<int> up;  // empty
  std::cout << up.get() << std::endl;
  up.reset (new int);       // takes ownership of pointer
  std::cout << up.get() << std::endl;
  *up=5;
  std::cout << *up << '\n';

  up.reset (new int);       // deletes managed object, acquires new pointer
  std::cout << up.get() << std::endl;
  *up=10;
  std::cout << *up << '\n';

  up.reset();               // deletes managed object
  std::cout << up.get() << std::endl;

  foo *p1 = new foo(10);
  std::unique_ptr<foo>p2 = std::make_unique<foo>(20);

  std::cout << p1 << std::endl;
  std::cout << p2.get() << std::endl;

  p2.reset(p1);  // p2 will point to p1 and p2 will get destroy
  std::cout << p1 << std::endl;
  std::cout << p2.get() << std::endl;

  return 0;
}
```

###### Output
```sh
0
0x505348
5
0x505358
10
0
0x505348
0x505358
~foo called
0x505348
0x505348
~foo called
```
#### std::unique_ptr::swap()
###### Syntax
```cpp
void swap (unique_ptr& x) noexcept;
```
where x is another `std::unique_ptr` object of the same type (i.e., with the same class template parameters).

Exchanges(Swap content) the contents of the `std::unique_ptr` object with those of x, transferring ownership of any managed object between them without destroying either.

The function swaps the respective stored pointers and stored deleters by invoking swap on them.

###### Example
```cpp
// unique_ptr::swap() example
#include <iostream>
#include <memory>

int main () {
  std::unique_ptr<int> foo (new int(10));
  std::unique_ptr<int> bar (new int(20));

  foo.swap(bar);

  std::cout << "foo: " << *foo << '\n';
  std::cout << "bar: " << *bar << '\n';

  return 0;
}
```

###### Output
```sh
20 
10 
```

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
    <a href="./smart_pointers.html" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="./shared_ptr.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---

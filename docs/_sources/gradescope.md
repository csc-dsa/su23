# Submission Notes

## Common C++ Errors

`````` {div} full-width
`````  {grid}
````   {grid-item-card}
Segmentation fault  
: This occurs when a program tries to access a memory location that it is not allowed to access. This can happen when accessing invalid pointers or arrays.

Array out of bounds  
: This error occurs when you try to access an array element outside the bounds of the array. This can lead to unpredictable behavior or crashes.  

Null pointer dereference 
: This occurs when you try to dereference a null pointer. This can happen when you forget to initialize a pointer or when you free a pointer and then try to access it.  

Memory leaks  
: This happens when you allocate memory dynamically and then forget to free it. This can lead to your program using up all available memory and crashing.
Use after free: This occurs when you free a pointer and then try to access it again. This can lead to unpredictable behavior or crashes.   

Uninitialized variable  
: This occurs when you use a variable without initializing it first. This can lead to unpredictable behavior.  

Type mismatch  
: This occurs when you try to assign a value of one type to a variable of a different type. This can lead to compiler errors or unpredictable behavior.  

Incorrect use of operators  
: This occurs when you use operators incorrectly, such as using the assignment operator instead of the equality operator.  

Incorrect function arguments  
: This occurs when you pass incorrect arguments to a function. This can lead to compiler errors or unpredictable behavior.  

Incorrect return type  
: This occurs when you declare a function with one return type but then return a value of a different type. This can lead to compiler errors or unpredictable behavior.  
````
````   {grid-item-card}
Double free  
: This occurs when you free a pointer more than once. This can lead to memory corruption and crashes. 

Incorrect use of loops  
: This occurs when you use loops incorrectly, such as using an infinite loop or using the wrong loop control variable.  

Incorrect use of pointers  
: This occurs when you use pointers incorrectly, such as dereferencing a null pointer or using a dangling pointer.  

Incorrect use of references  
: This occurs when you use references incorrectly, such as passing a reference to a temporary object or modifying a const reference.  

Incorrect use of templates  
: This occurs when you use templates incorrectly, such as not specifying template arguments or using non-template functions with template arguments.  

Incorrect use of namespaces  
: This occurs when you use namespaces incorrectly, such as not qualifying function or class names properly.  

Incorrect use of constructors or destructors  
: This occurs when you use constructors or destructors incorrectly, such as not properly initializing member variables or not freeing memory in the destructor.  

Incorrect use of inheritance  
: This occurs when you use inheritance incorrectly, such as not properly calling base class constructors or not using virtual functions when needed.  

Incorrect use of overloaded operators  
: This occurs when you overload operators incorrectly, such as not returning the correct type or not properly handling references.  

Incorrect use of STL containers  
: This occurs when you use STL containers incorrectly, such as not properly initializing them or accessing them incorrectly.  

````
`````
It is important to note that these are not the only possible errors when working with data structures in C++. It is always important to thoroughly test your code and ensure that it is working as intended.
``````

## Building LaTeX Statements

```` {div} full-width
``` {card}
Assignments 3 & 5 require the use of LaTeX to complete proofs and responses. Here is some formatting to get you started.
```

``` {list-table}
* - LaTeX Enclosure
  - $$  $$
  - \$\$  \$\$
* -
  - 
  - 
* - Summation Symbol
  - $$ \sum $$
  - \$\$ \sum \$\$
* - Summation Notation
  - $$ \sum_{k=1}^{n} a_k $$
  - \$\$ \sum_{k=1}^{n} a_k \$\$
* -
  - 
  - 
* - fractions
  - $$ \frac{n}{d} $$
  - \$\$ \frac{n}{d} \$\$
* - superscripts
  - $$ a^{k} $$
  - \$\$ a^{k} \$\$
* - subscripts
  - $$ a_{k} $$
  - \$\$ a_{k} \$\$

```
````
<style>
  .red {color:red}
  .blue {color:blue}
  .green {color:green}
  .orange {color:darkorange}
  .purple {color:purple}
  .brown {color:brown}
  .fa-rocket {display: none;}
</style>

# Dynamic Arrays

````` {div} full-width
```` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/MwwbgqG6bSk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Dynamic arrays are a common data structure used in computer programming to store a collection of elements of the same type. Unlike static arrays, which have a fixed size that cannot be changed at runtime, dynamic arrays can grow or shrink as needed.

In a dynamic array, the elements are stored in contiguous memory locations, just like in a static array. However, a dynamic array has additional memory allocated beyond its initial size to allow for growth. When the dynamic array is full, it can be resized by allocating a new block of memory with a larger size and copying the existing elements into the new block. This process is called resizing.

Dynamic arrays are widely used because they provide a balance between the fast random access provided by static arrays and the flexibility of linked lists. They are particularly useful when the size of the collection is unknown or unpredictable at compile time. Dynamic arrays are commonly used in many algorithms, such as sorting and searching, where efficient random access to elements is important.

However, resizing a dynamic array can be an expensive operation, particularly when the array is large and the resizing occurs frequently. Therefore, careful consideration of the size of the dynamic array and the frequency of resizing is necessary when designing programs that use dynamic arrays.
```

``` {card} Additional Resources
- []()
```
`````

## Arrays

`````````` {div} full-width
````````   {tab-set}
```````    {tab-item} Definition
```` {card} 

- An array is a **contiguous** sequence of elements of the <b class="green">same type</b>
- Each element can be accessed using <b class="green">index</b>

+++

- Array Name: $A$
- Array Length: $n$

``` {figure} https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fprepinsta.com%2Fwp-content%2Fuploads%2F2020%2F11%2Farrays-in-c.jpg&f=1&nofb=1&ipt=1002190a76932a376f3a7bf8699c349d3ce7811177409ad11bc1ae1d14614a0b&ipo=images
```
<!-- 
``` {image} imgs/05_s04.png
:align: center
``` -->

$$note:\ all\ elements\ of\ the\ same\ data\ type$$

````
```````
```````    {tab-item} Declaration
```` {card} 

```cpp
//array declaration by specifying size  
int myarray1[100];

//can also declare an array of user specified
//size (must be const for many compilers!)  
int n = 8;
int myarray2[n];

// can declare and initialize elements  
double arr[] = { 10.0, 20.0, 30.0, 40.0 };
// size is implicitly understood by the compiler when initialized at declaration

// alternative way  
int arr[5] = { 1, 2, 3 };
// size is explicitly manipulated for the compiler
// size = 5, element count = 3, empty elements remaining = 2 

```

````
```````
````````

``````````


### Static arrays

````` {div} full-width
```` {card}
So far... we have seen examples of arrays, <b class="brown">allocated in the stack</b> (fixed length)

```cpp
//array declaration by specifying size  
int myarray1[100];
```

You can allocate memory dynamically, <b class="brown">allocated in the heap</b> (still fixed length)

```cpp
int *myarray = new int[100];
//...
//work with the array
//...
delete []myarray;
```
````
`````

## Memory Allocation

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Layout
``` {admonition} Memory layout of C/C++ programs
:class: tip

![](https://media.geeksforgeeks.org/wp-content/uploads/memoryLayoutC.jpg)

[https://www.geeksforgeeks.org/memory-layout-of-c-program/](https://www.geeksforgeeks.org/memory-layout-of-c-program/)

```
```````
```````    {tab-item} Background
Memory allocation is an essential aspect of data structures and algorithms as it determines how memory is allocated and used to store data. Data structures are designed to efficiently organize and store data in memory, and algorithms use these data structures to perform operations on the data.

In general, there are two types of memory allocation: static and dynamic. Static memory allocation refers to memory allocation that is fixed at compile-time and cannot be changed at runtime. This is typically used for variables that have a fixed size and do not need to be resized during program execution.

Dynamic memory allocation, on the other hand, refers to memory allocation that is done at runtime and can be resized as needed. This is typically used for data structures that need to grow or shrink in size as data is added or removed.

One common data structure that uses dynamic memory allocation is the linked list. In a linked list, each element in the list is stored in a node that contains a pointer to the next node in the list. The nodes can be dynamically allocated as needed, allowing the list to grow or shrink as data is added or removed.

Another common data structure that uses dynamic memory allocation is the dynamic array. In a dynamic array, the size of the array can be dynamically resized as needed, allowing for efficient memory usage.

Memory allocation is an important consideration when designing and implementing data structures and algorithms. Efficient memory usage can greatly improve the performance of an algorithm, while inefficient memory usage can lead to performance problems or even crashes. Therefore, it is important to carefully consider the memory requirements of a data structure or algorithm and optimize memory usage wherever possible.
```````
```````    {tab-item} Visualization
<iframe width="1000" height="600" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=//%20Example%20C%2B%2B%20code%20for%20OPT%0Aint%20main%28%29%20%7B%0A%20%20float%20var1%3B%0A%20%20float%20var2%3B%0A%20%20int%20static_array%5B10%5D%3B%0A%20%20int%20*static_array_heap%20%3D%20new%20int%20%5B10%5D%3B%0A%20%20//%20...%0A%20%20//%20work%20with%20this%20array%0A%20%20//%20...%0A%20%20delete%20%5B%5D%20static_array_heap%3B%0A%20%20return%200%3B%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
```````
```````    {tab-item} Notes
````` {admonition} A few notes...
:class: tip

```` {admonition} Creating variables in the stack

- variables are automatically created and freed
- variables only exist while the function is running
- faster and good for small local variables
````
```` {admonition} Allocating memory in the heap

- memory is allocated at runtime
- programmer is responsible for allocating/de-allocating memory
- variables can be accessed globally (in the program)
- memory may become fragmented
- slower but good for large variables
````

`````
```````
```````    {tab-item} What if
````` {admonition} What if...?
:class: attention

``` {admonition} Case 1
:class: note

We don't know the max size of an array before running the program!

- user specified inputs/decisions!
- e.g. read an image or video and display

```

``` {admonition} Case 2
:class: note

The sequence changes over time (during the  execution of the program)

- e.g. you develop a text editor and represent the sequence of characters as an array

```

``` {admonition} Question
:class: attention

Which data structure (studied so far) would you use in each case?
```
`````
```````
````````
`````````
``````````

## [Dynamic Arrays](https://www.enjoyalgorithms.com/blog/dynamic-array)


````` {div} full-width
```` {card}

**Dynamically allocated arrays that change their size over time**

- can <b class="orange">grow</b> automatically
- can <b class="orange">shrink</b> automatically

**Operations on arrays**

- `append`
- `remove_last`
- `get`  $\Theta(1)$
- `set`  $\Theta(1)$

````
`````

### First try

````` {div} full-width
```` {card}

**Start with an empty array**  

**For every *_append_*:**

- increase the size of the array by 1 then write the new element

**For every *_remove_last_*:**

- remove the last element and then decrease the size of the array by 1
````
`````

### Analyzing cost

````````` {div} full-width
```````` {card}
```````  {tab-set}
``````   {tab-item} Grow by 1
Count array accesses (reads and writes) of adding first $n$ elements

- will ignore the cost of allocating/de-allocating arrays

````` {grid}

```` {grid-item-card}

``` {list-table}
:header-rows: 1

* - $n$
  - $append$
  - $copy$
* -
  -
  -
* -
  -
  -
* - 
  - 
  - 
* - 
  - 
  - 
* - 
  - 
  - 
* -
  -
  -
* -
  -
  -
* - 
  - 
  - 
* - 
  - 
  - 
* - 
  - 
  - 

```

````

```` {grid-item-card}

``` {card}
Each row indicates the number of **reads and writes** necessary for appending an element into an **existing array of length $n$**
```

$$n + \sum_{i=0}^{n-1} i^2 = n + n^2 - n$$

$$\Theta(n^2)$$

````

`````
``````
``````   {tab-item} Doubling array
Count array accesses (reads and writes) of adding first $n = 2^i$ elements

- will ignore the cost of allocating/de-allocating arrays

````` {grid}

```` {grid-item-card}

``` {figure} https://cdn-images-1.medium.com/max/960/1*9s7_mGUIzA_JcOOw-zQh9Q.png
[https://www.enjoyalgorithms.com/blog/dynamic-array](https://www.enjoyalgorithms.com/blog/dynamic-array)
```

````

```` {grid-item-card}

``` {card}
Each row indicates the number of **reads and writes** necessary for appending an element into an **existing array of length $n$**
```

$$n + \sum_{i = 1}^{log\ n} 2^i = n + 2^{log\ n + 1} - 1$$

$$\Theta(n)$$

$$\sum_{i=0}^n c^i = \frac{c^{n^2 + 1} - 1}{c - 1}$$

````
`````
``````
`````` {tab-item} Proof
``` {figure} imgs/05_s20.png
```
`````` 
```````
````````
`````````
<!-- 
### Worst-case and average-case

````` {div} full-width
```` {card}
``` {dropdown} Analysis for appending a *single element* using increase-by-1
$$\Theta(n^2)$$
```

``` {dropdown} Analysis for appending a *single element* using repeated doubling
$$\Theta(n)$$
```
```` -->

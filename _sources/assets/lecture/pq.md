<style>
  .red {color:red}
  .blue {color:blue}
  .green {color:green}
  .orange {color:darkorange}
  .purple {color:purple}
  .brown {color:brown}
  .fa-rocket {display: none;}
</style>

# Priority Queues

``````````` {div} full-width
``````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/wptevk0bshY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A priority queue is an abstract data type in computer science that stores a collection of elements with associated priorities, and provides operations for adding and removing elements in a way that respects their priorities.

A priority queue is similar to a queue data structure, but unlike a queue, the order in which elements are removed from a priority queue is based on their priority rather than their order of insertion. In other words, the element with the highest priority is removed first, regardless of when it was added to the priority queue.

Priority queues are commonly used in applications where tasks or events have different levels of importance, such as task scheduling, event-driven simulations, and network routing protocols.

Priority queues can be implemented using various data structures, such as arrays, linked lists, heaps, and binary search trees. However, heap-based implementations are the most common, as they provide efficient $O(log\ n)$ time complexity for both insertion and removal operations, making them suitable for large collections.
```

``` {card} Additional Resources
- [Priority Queues | davefeinberg](https://youtu.be/5HC6qrWGrpA)
- [Priority Queues 2 | davefeinberg](https://youtu.be/2iSJJSci5u4)
- [Priority Queues 3 | davefeinberg](https://youtu.be/fFbtftih_eY)
- [Priority Queues 4 | davefeinberg](https://youtu.be/ujbhsL1Ngg8)
```
```````
```````````

## Definitions

``````````` {div} full-width
```` {card}

``` {card}
Collections
: Insert and delete items. Which items to delete?
```

``` {card}
Stack
: Remove the item most recently added

Queue
: Remove the item least recently added

Randomized Queue
: Remove a random item

Generalizes
: stack, queue, randomized queue
```

``` {card}
Priority Queue
: Remove the largest (or smallest) item
```

````
```````````

## [Queues](https://www.geeksforgeeks.org/queue-data-structure/?ref=gcse)

``````````` {div} full-width
```` {card}
``` {image} https://miro.medium.com/max/3148/0*TRbfsq86lqDoqW6b.png
```
````
```````````

## [Priority Queue](https://www.geeksforgeeks.org/priority-queue-set-1-introduction/)

``````````` {div} full-width
```` {card}
``` {image} https://netmatze.files.wordpress.com/2014/08/priorityqueue.png
```
````
```````````

## [Applications](https://www.geeksforgeeks.org/applications-priority-queue/)

`````` {div} full-width
````` {grid}
:padding: 2 2 2 2
```` {grid-item-card} pq huffman tree
:columns: 4
``` {image} https://forum.nwoods.com/uploads/db3963/optimized/2X/a/aee3daf4aaa56da16df5f083c5c6f5a3c8324eb8_2_1024x749.png
:width: 100%
```
````
```` {grid-item-card} network routing
:columns: 4
``` {image} https://cdncontribute.geeksforgeeks.org/wp-content/uploads/DVP1.jpg
:width: 100%
```
````
```` {grid-item-card} process scheduling
:columns: 4
``` {image} https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https:%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F2110D84751C24CE41C
:width: 100%
```
````
```` {grid-item-card} Other examples...
:columns: 12
- Artificial Intelligence (search)
- Graph Algorithms
- Stream Data Algorithms
- HPC Task Scheduling
````
`````
``````

### Priority Queues

````` {div} full-width
```` {card}
**Collections of $<key, value>$ pairs**
- *_keys_* are objects on which an *_order_* is defined

Every pair of keys must be comparable according to a *_total order_*:
````
`````

`````` {div} full-width
````` {card} Properties
```` {grid}
``` {grid-item-card} Reflexive
$$k_1 \le k_2$$
```
``` {grid-item-card} Antisymmetric
$$k_1 \le\ k_2 \ \ \ \land \ \ \ k_2 \le k_1$$
$$\Rightarrow$$
$$k_1 = k_2$$
```
``` {grid-item-card} Transitive
$$k_1 \le k_2 \ \ \ \land \ \ \ k_2 \le k_3$$
$$\Rightarrow$$
$$k_1 \le k_3$$
```
````
`````
``````

`````` {div} full-width
````` {grid}
```` {grid-item-card} Queues
:columns: 6
- basic operations: 
  - *_$enqueue$_*, *_$dequeue$_*
- always remove the item least recently added
````
```` {grid-item-card} Priority Queues
:columns: 6
- basic operations: 
  - *_$insert$_*, *_$removeMax$_*
- MaxPQ: 
  - always remove the item with the highest (max) priority
- MinPQ: 
  - always remove the item with the lowest (min) priority
````
```` {grid-item-card}
:columns: 12
``` {image} https://studyalgorithms.com/wp-content/uploads/2013/12/priority_queue.png
:align: center
```
````
`````
``````

`````` {div} full-width
``` {figure} https://media.geeksforgeeks.org/wp-content/cdn-uploads/Priority-Queue-min-1024x512.png
:width: 100%
Working with PQ's
```
``````


### Performance

``````````` {div} full-width
```` {card}
``` {list-table}
:header-rows: 1

* -
  - Sorted Array/List
  - Unsorted Array/List
* - insert
  - $O(n)$<br><br>must find place where to insert item
  - $O(1)$<br><br>item can be inserted at head or tail
* - removeMax<br>max
  - $O(1)$<br><br>largest/smallest key is at:<br> $arr[0]$/$arr[n-1]$
  - $O(n)$<br><br>must traverse entire sequence to find largest/smallest
```
````
```````````

### cppreference.com

`````` {div} full-width

<iframe src="https://en.cppreference.com/w/cpp/container/priority_queue" frameborder="0" width="100%" height="800"></iframe>

``````

## Heaps

### [(max) Heap](https://www.geeksforgeeks.org/difference-between-min-heap-and-max-heap/?ref=gcse)

``````````` {div} full-width
``` {card}
Structure Property
: a heap is a [*_complete binary tree_*](https://www.geeksforgeeks.org/complete-binary-tree/)

Heap-Order Property
: for every node $x$:
  - $key\ parent\ x\ \ge\ key \ x$
  - except the root, which has no parent
```

``` {image} https://media.geeksforgeeks.org/wp-content/uploads/20201106115254/MaxHeap.jpg
```
```````````

### [Height of a heap](https://www.geeksforgeeks.org/height-complete-binary-tree-heap-n-nodes/)

``````````` {div} full-width
```` {card}

What is the minimum number of nodes in a complete binary tree of height $h$?

``` {image} https://media.geeksforgeeks.org/wp-content/uploads/20201106115254/MaxHeap.jpg
```

$$n \ge 2^h\Rightarrow\ log\ n \ge log\ 2^h \Rightarrow\ log\ n \ge h$$
````
```````````

## Implementation

``````````` {div} full-width
``````` {card}
````` {grid}
```` {grid-item-card}
:columns: 12
``` {image} imgs/13_implement_2.png
```
````
```` {grid-item-card}
:columns: 12
``` {image} imgs/13_implement_1.png
```
````
``` {grid-item-card}
node(i)
: $$i$$
```
``` {grid-item-card}
parent(i)
: $$floor(\frac{i}{2})$$
```
``` {grid-item-card}
left_child(i)
: $$i * 2$$
```
``` {grid-item-card}
right_child(i)
: $$i * 2 + 1$$
```
`````
```````
```````````

````````` {div} full-width
```````` {grid}
``````` {grid-item-card}
$insert$

**Append new element to the end of array**

Check heap-order property
: if <b class="red">violated, *_Up-Heap_*</b> (swap with parent)
  : **repeat** until heap-order is restored
: if <b class="green">not</b>, $insert$ complete

Time Complexity
: $O(log\ n)$
```````
``````` {grid-item-card}
$removeMax$

Max element is the first element of the array
: the $root$ of the heap

Copy last element of array to the first position
: then decrement array size by 1 (removes the last element)

Check heap-order property
: if <b class="red">violated, _Down-Heap_</b> (swap with **larger** child)
  : **repeat** until heap-order is restored
: if <b class="green">not</b>, *_insert_* complete

Time Complexity
: $O(log\ n)$
```````
````````
`````````

``` {div} full-width
<iframe src="https://visualgo.net/en/heap" width="100%" height="800"></iframe>
```

## Performance

``````````` {div} full-width
```` {card}

``` {list-table}
:header-rows: 1

* - 
  - Sorted Array/List
  - Unsorted Array/List
  - Heap
* - insert
  - $O(n)$
  - $O(1)$
  - $O(log\ n)$
* - removeMax
  - $O(1)$
  - $O(n)$
  - $O(log\ n)$
* - max
  - $O(1)$
  - $O(n)$
  - $O(1)$
* - insert N
  - $O(n^2)$
  - $O(n)$
  - $O(n)^{**}$
```

(**) assuming we know the sequence in advance (*_buildHeap_*)

````
```````````



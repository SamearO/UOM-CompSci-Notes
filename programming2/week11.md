# Data Structures II

# HashMaps

* `HashMap` is a data structure that uses a hashing mechanism (a mechanism to deterministically get 1 value from another, usually a `String` to an `int`) to create a dictionary of key value pairs.
* It uses the hash value to choose where to store or retrieve the data.

## HashMap implementation
1. It creates an `ArrayList` to store the data.
2. It hashes the key, a hashable type like a `String` and converts it to an `int`.
3. The `int` is used as an index to the `ArrayList` and thus the value is stored in the `ArrayList` in that index. 
4. Sometimes, keys can have the same result when passing through the hashing function, this leads to a hash collision
5. Hence when adding elements to a specific index, the element is passed as a node in a `Linked List` wherein the node contains the value as well as a pointer to the next element in the list.
6. Thus if an item already exists at that index, the item's pointer points to the location of the new element to add at that index.
7. Hence to receive an element, hash the key, use the hash to get the index and use the key to compare each node in the linked list to retrieve the value.

## HashSet

A `HashSet` is an implementation of `Set` that uses `HashMap` to ensure that there are no duplicates as `HashMap`s prevent duplicate keys. Thus if a key of the `HashMap` contains the present value, that value exists in the set. 
```java 
// HashSet Implementation.
class HashSet {
    public static final Object PRESENT  = new Object();
    
    public HashSet() {
        map = new HashMap<>();
    }

    public boolean add(E e) {
        return this.map.put(e, PRESENT) == null;
    }
}

```

# Sorting
* Sorting can be done with various algorithms however the most important implementation detail for sorting objects is how to compare them.
* Java's `java.util.Collections.sort` function requires a method that implements either `Comparator` or `Comparable` to return a negative integer if an object is smaller than another, 0 if they are equal or a positive integer if an object is larger than another. 
* `Comparable` is used when there is only 1 natural sort order. `Comparator` is used when there are multiple valid sort orders.

## Comparable implementations
```java 
// Using Comparable to sort Integers
import java.util.Comparable;

class Integer implements Comparable {
    int value;

    public int compareTo(Integer toCompare) {
        return this.value - toCompare.value;
    }
}
ArrayList<Integer> myArray = new ArrayList<Integer>();
// Add Values here
Collections.sort(myArray) 
```

## Comparator implementation
```java
import java.util.Comparator;
// Using Comparator to sort Books by page length
class BookPageComparator implements Comparator {
    public int compare (Book book1, Book book2) {
        return book1.pageCount() - book2.pageCount(); 
    }
}

List<Book> myList = new ArrayList<Book>();
Collections.sort(myList, new BookPageComparator());
```

# Recursion
* Recursion is when a function calls itself, it requires a base case that returns a simple output as well as a reducing case that reduces higher order calls of the function to a lower order call, calling itself with different inputs to eventually reach the base case
* Recursive functions can reach a `StackOverflow` error when they have recursed too many times and the stack pointer overflows.

```java 
// A function to recursively calculate the fibonnaci number at an index of the fib sequence
public int fib(n) {
    if (n <= 1) {
        return n;
    } else {
        return (fib(n-1) + fib(n-2));
    }
}
```

# Trees
<img src="./img/binary_search_tree.png" alt="drawing" width="50%"/>

## Binary Trees
* `Binary Trees` are tree structures that have a root node and each node has at most 2 child nodes.

## Binary Search Trees
* `Binary Search Trees` are `Binary Trees` who's nodes child nodes are ordered such that child values smaller than the node are on the left and values larger than the node are on the right.
* To find if an element is in the tree, start at the root node, if it is larger then go on the right, if smaller go on the left. If equal then it is found. 
* Do this until reaching a leaf node (not found) or the value is found. 
* The same concept can be used to add to a `BST`.
* To remove an element, do a search to find the next biggest value in the tree, then replace the deleted node with the value. 

## Breadth First vs Depth First Traversal
* `BFS` is when all the children of a root are searched before moving on to the grandchildren and so on. 
* `DFS` can be done in either a `Pre Order Traversal`, `In Order Traversal` or `Post Order Traversal`.

## Depth First Traversal Methods
* Pre Order Traversal: Visit the root, Traverse down the left of a root node. Then starting at the right node of the root node, do the pre-order traversal again.
* In Order Traversal: Traverse the left, then root then right. This is useful for getting the nodes in a decreasing order
* Post Order Traversal: Visit the left, then right, then root.
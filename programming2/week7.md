# Data Structures

Types of lists:
* `ArrayList` Can be used to create a list of objects and the length of the array can be arbitrarily increased or decreased. Elements can be added, removed and shuffled at any point in the array
* `Stack` is a last in first out array that has a stack pointer that points to the top element in the stack. Elements are added by pushing and removed by popping
* `Queue` is a first in first out array, thus elements are added in at one end and removed at the other. 
* A set is an array that only contains unique values. Any duplicates are not added to the set.

```java
//Creating an ArrayList
import java.util.ArrayList;

ArrayList<String> myStringArray = new ArrayList<String>();
myStringArray.add("Element");
```

## ArrayList Implementation Details

* ArrayLists are just a wrapper around `Object[]` and thus have no inherent traits that make it possible to resize. 
* An ArrayList starts with a default size of 10 and when it exceeds its limit, a new `Object[]` is created with a multiple of the size and all the existing elements are carried over. 
* Thus there is sometimes a large overhead when adding items to the ArrayList. This overhead can be encountered multiple times when creating a large ArrayList
* Hence when creating ArrayLists that are known to be large, pass an integer as its initial capacity as shown:

```java
ArrayList<String> largeArray = new ArrayList<String>(100);
```
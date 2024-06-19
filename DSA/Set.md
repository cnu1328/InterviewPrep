# Sets in C++ and Java

## Introduction

A set is a data structure that stores unique elements in a specific order (in the case of `std::set` in C++) or in an undefined order (in the case of `std::unordered_set` in C++). Sets are used to perform operations such as searching for an element, inserting an element, and deleting an element efficiently.

## Sets in C++

### Overview

In C++, the Standard Template Library (STL) provides two types of sets:
- `std::set`: Implements a balanced binary search tree (typically a Red-Black Tree), which keeps elements in sorted order.
- `std::unordered_set`: Implements a hash table, which keeps elements in an arbitrary order and provides average constant-time complexity for most operations.

### Functionalities

#### `std::set`

1. **Insertion**: Adds an element to the set.
   ```cpp
   std::set<int> mySet;
   mySet.insert(10);
   ```

2. **Deletion**: Removes an element from the set.
   ```cpp
   mySet.erase(10);
   ```

3. **Search**: Finds an element in the set.
   ```cpp
   auto it = mySet.find(10);
   if (it != mySet.end()) {
       // Element found
   }
   ```

4. **Traversal**: Iterates through elements in sorted order.
   ```cpp
   for (const int& elem : mySet) {
       std::cout << elem << " ";
   }
   ```

#### `std::unordered_set`

1. **Insertion**: Adds an element to the set.
   ```cpp
   std::unordered_set<int> myUnorderedSet;
   myUnorderedSet.insert(10);
   ```

2. **Deletion**: Removes an element from the set.
   ```cpp
   myUnorderedSet.erase(10);
   ```

3. **Search**: Finds an element in the set.
   ```cpp
   auto it = myUnorderedSet.find(10);
   if (it != myUnorderedSet.end()) {
       // Element found
   }
   ```

4. **Traversal**: Iterates through elements in an undefined order.
   ```cpp
   for (const int& elem : myUnorderedSet) {
       std::cout << elem << " ";
   }
   ```

### Time and Space Complexity

#### `std::set`

- **Insertion**: O(log n)
- **Deletion**: O(log n)
- **Search**: O(log n)
- **Space Complexity**: O(n)

#### `std::unordered_set`

- **Insertion**: O(1) on average
- **Deletion**: O(1) on average
- **Search**: O(1) on average
- **Space Complexity**: O(n)

### Example

```cpp
#include <iostream>
#include <set>
#include <unordered_set>

int main() {
    // Example with std::set
    std::set<int> mySet;
    mySet.insert(1);
    mySet.insert(2);
    mySet.insert(3);
    mySet.insert(2); // Duplicate, will not be added

    std::cout << "std::set elements in sorted order: ";
    for (const int& elem : mySet) {
        std::cout << elem << " ";
    }
    std::cout << std::endl;

    // Example with std::unordered_set
    std::unordered_set<int> myUnorderedSet;
    myUnorderedSet.insert(1);
    myUnorderedSet.insert(2);
    myUnorderedSet.insert(3);
    myUnorderedSet.insert(2); // Duplicate, will not be added

    std::cout << "std::unordered_set elements in arbitrary order: ";
    for (const int& elem : myUnorderedSet) {
        std::cout << elem << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

## Sets in Java

### Overview

In Java, the `Set` interface is part of the Java Collections Framework and is implemented by classes such as `HashSet`, `LinkedHashSet`, and `TreeSet`.

- **`HashSet`**: Implements a set backed by a hash table.
- **`LinkedHashSet`**: Implements a set with predictable iteration order, maintained by a doubly-linked list.
- **`TreeSet`**: Implements a set backed by a TreeMap, which keeps elements in sorted order.

### Functionalities

#### `HashSet`

1. **Insertion**: Adds an element to the set.
   ```java
   Set<Integer> hashSet = new HashSet<>();
   hashSet.add(10);
   ```

2. **Deletion**: Removes an element from the set.
   ```java
   hashSet.remove(10);
   ```

3. **Search**: Checks if an element is in the set.
   ```java
   if (hashSet.contains(10)) {
       // Element found
   }
   ```

4. **Traversal**: Iterates through elements in arbitrary order.
   ```java
   for (Integer elem : hashSet) {
       System.out.println(elem);
   }
   ```

#### `TreeSet`

1. **Insertion**: Adds an element to the set.
   ```java
   Set<Integer> treeSet = new TreeSet<>();
   treeSet.add(10);
   ```

2. **Deletion**: Removes an element from the set.
   ```java
   treeSet.remove(10);
   ```

3. **Search**: Checks if an element is in the set.
   ```java
   if (treeSet.contains(10)) {
       // Element found
   }
   ```

4. **Traversal**: Iterates through elements in sorted order.
   ```java
   for (Integer elem : treeSet) {
       System.out.println(elem);
   }
   ```

### Time and Space Complexity

#### `HashSet`

- **Insertion**: O(1) on average
- **Deletion**: O(1) on average
- **Search**: O(1) on average
- **Space Complexity**: O(n)

#### `TreeSet`

- **Insertion**: O(log n)
- **Deletion**: O(log n)
- **Search**: O(log n)
- **Space Complexity**: O(n)

### Example

```java
import java.util.HashSet;
import java.util.Set;
import java.util.TreeSet;

public class Main {
    public static void main(String[] args) {
        // Example with HashSet
        Set<Integer> hashSet = new HashSet<>();
        hashSet.add(1);
        hashSet.add(2);
        hashSet.add(3);
        hashSet.add(2); // Duplicate, will not be added

        System.out.println("HashSet elements in arbitrary order: ");
        for (Integer elem : hashSet) {
            System.out.println(elem);
        }

        // Example with TreeSet
        Set<Integer> treeSet = new TreeSet<>();
        treeSet.add(1);
        treeSet.add(2);
        treeSet.add(3);
        treeSet.add(2); // Duplicate, will not be added

        System.out.println("TreeSet elements in sorted order: ");
        for (Integer elem : treeSet) {
            System.out.println(elem);
        }
    }
}
```

## Conclusion

Sets are powerful data structures for managing collections of unique elements. In C++, you can use `std::set` and `std::unordered_set` depending on your need for ordered or unordered storage. In Java, you can choose between `HashSet` and `TreeSet` based on whether you need order or not. Understanding the time and space complexities helps in choosing the right set implementation for your use case.
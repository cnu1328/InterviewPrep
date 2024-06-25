# Maps and HashMaps in C++, Java, and JavaScript

## Introduction

Maps and HashMaps are data structures that store key-value pairs. They allow for efficient retrieval, insertion, and deletion of elements based on keys. The keys in a map are unique, and each key maps to a single value.

## Maps in C++

### Overview

In C++, the Standard Template Library (STL) provides two main types of associative containers:
- **`std::map`**: Implements a balanced binary search tree (usually a Red-Black Tree), which keeps elements in sorted order.
- **`std::unordered_map`**: Implements a hash table, which keeps elements in an arbitrary order.

### Functionalities

#### `std::map`

1. **Insertion**: Adds a key-value pair to the map.
   ```cpp
   std::map<int, std::string> myMap;
   myMap.insert(std::make_pair(1, "one"));
   myMap[2] = "two";
   ```

2. **Deletion**: Removes a key-value pair from the map.
   ```cpp
   myMap.erase(1);
   ```

3. **Search**: Finds the value associated with a key.
   ```cpp
   auto it = myMap.find(2);
   if (it != myMap.end()) {
       std::cout << "Key 2 has value " << it->second << std::endl;
   }
   ```

4. **Traversal**: Iterates through all key-value pairs in sorted order of keys.
   ```cpp
   for (const auto& pair : myMap) {
       std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
   }
   ```

#### `std::unordered_map`

1. **Insertion**: Adds a key-value pair to the map.
   ```cpp
   std::unordered_map<int, std::string> myUnorderedMap;
   myUnorderedMap.insert(std::make_pair(1, "one"));
   myUnorderedMap[2] = "two";
   ```

2. **Deletion**: Removes a key-value pair from the map.
   ```cpp
   myUnorderedMap.erase(1);
   ```

3. **Search**: Finds the value associated with a key.
   ```cpp
   auto it = myUnorderedMap.find(2);
   if (it != myUnorderedMap.end()) {
       std::cout << "Key 2 has value " << it->second << std::endl;
   }
   ```

4. **Traversal**: Iterates through all key-value pairs in arbitrary order.
   ```cpp
   for (const auto& pair : myUnorderedMap) {
       std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
   }
   ```

### Time and Space Complexity

#### `std::map`

- **Insertion**: O(log n) - Because it uses a balanced tree, insertion requires finding the correct place in the tree.
- **Deletion**: O(log n) - Similar to insertion, it requires finding the node and then rebalancing the tree.
- **Search**: O(log n) - The search operation traverses the tree to find the element.
- **Space Complexity**: O(n) - Each element is stored in a node in the tree, so the space complexity is linear with respect to the number of elements.

#### `std::unordered_map`

- **Insertion**: O(1) on average - Uses a hash function to place elements, leading to average constant time complexity.
- **Deletion**: O(1) on average - Similar to insertion, it uses the hash function to find and remove elements.
- **Search**: O(1) on average - Uses the hash function to locate elements quickly.
- **Space Complexity**: O(n) - Space required is proportional to the number of elements, plus some overhead for the hash table structure.

### Example

```cpp
#include <iostream>
#include <map>
#include <unordered_map>

int main() {
    // Example with std::map
    std::map<int, std::string> myMap;
    myMap[1] = "one";
    myMap[2] = "two";
    myMap[3] = "three";

    std::cout << "std::map elements in sorted order: " << std::endl;
    for (const auto& pair : myMap) {
        std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
    }

    // Example with std::unordered_map
    std::unordered_map<int, std::string> myUnorderedMap;
    myUnorderedMap[1] = "one";
    myUnorderedMap[2] = "two";
    myUnorderedMap[3] = "three";

    std::cout << "std::unordered_map elements in arbitrary order: " << std::endl;
    for (const auto& pair : myUnorderedMap) {
        std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
    }

    return 0;
}
```

## Maps in Java

### Overview

In Java, the `Map` interface is part of the Java Collections Framework and is implemented by classes such as `HashMap`, `LinkedHashMap`, and `TreeMap`.

- **`HashMap`**: Implements a set backed by a hash table.
- **`LinkedHashMap`**: Implements a set with predictable iteration order, maintained by a doubly-linked list.
- **`TreeMap`**: Implements a set backed by a TreeMap, which keeps elements in sorted order.

### Functionalities

#### `HashMap`

1. **Insertion**: Adds a key-value pair to the map.
   ```java
   Map<Integer, String> hashMap = new HashMap<>();
   hashMap.put(1, "one");
   hashMap.put(2, "two");
   ```

2. **Deletion**: Removes a key-value pair from the map.
   ```java
   hashMap.remove(1);
   ```

3. **Search**: Checks if a key is in the map.
   ```java
   if (hashMap.containsKey(2)) {
       System.out.println("Key 2 has value " + hashMap.get(2));
   }
   ```

4. **Traversal**: Iterates through all key-value pairs in arbitrary order.
   ```java
   for (Map.Entry<Integer, String> entry : hashMap.entrySet()) {
       System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
   }
   ```

#### `TreeMap`

1. **Insertion**: Adds a key-value pair to the map.
   ```java
   Map<Integer, String> treeMap = new TreeMap<>();
   treeMap.put(1, "one");
   treeMap.put(2, "two");
   ```

2. **Deletion**: Removes a key-value pair from the map.
   ```java
   treeMap.remove(1);
   ```

3. **Search**: Checks if a key is in the map.
   ```java
   if (treeMap.containsKey(2)) {
       System.out.println("Key 2 has value " + treeMap.get(2));
   }
   ```

4. **Traversal**: Iterates through all key-value pairs in sorted order.
   ```java
   for (Map.Entry<Integer, String> entry : treeMap.entrySet()) {
       System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
   }
   ```

5. **Get Paricular Key Value**: 

```Java
    // To get the value of a key
    map.get(keyValue);

    // To increment the value of a key
    map.put(keyValue, map.getOrDefault(keyValue, 0) + 1);
```

### Time and Space Complexity

#### `HashMap`

- **Insertion**: O(1) on average - Uses a hash function to place elements, leading to average constant time complexity.
- **Deletion**: O(1) on average - Similar to insertion, it uses the hash function to find and remove elements.
- **Search**: O(1) on average - Uses the hash function to locate elements quickly.
- **Space Complexity**: O(n) - Space required is proportional to the number of elements, plus some overhead for the hash table structure.

#### `TreeMap`

- **Insertion**: O(log n) - Because it uses a balanced tree, insertion requires finding the correct place in the tree.
- **Deletion**: O(log n) - Similar to insertion, it requires finding the node and then rebalancing the tree.
- **Search**: O(log n) - The search operation traverses the tree to find the element.
- **Space Complexity**: O(n) - Each element is stored in a node in the tree, so the space complexity is linear with respect to the number of elements.

### Example

```java
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;

public class Main {
    public static void main(String[] args) {
        // Example with HashMap
        Map<Integer, String> hashMap = new HashMap<>();
        hashMap.put(1, "one");
        hashMap.put(2, "two");
        hashMap.put(3, "three");

        System.out.println("HashMap elements in arbitrary order: ");
        for (Map.Entry<Integer, String> entry : hashMap.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }

        // Example with TreeMap


        Map<Integer, String> treeMap = new TreeMap<>();
        treeMap.put(1, "one");
        treeMap.put(2, "two");
        treeMap.put(3, "three");

        System.out.println("TreeMap elements in sorted order: ");
        for (Map.Entry<Integer, String> entry : treeMap.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }
    }
}
```

## Maps in JavaScript

### Overview

In JavaScript, the `Map` object is a built-in object that allows you to store key-value pairs and remembers the original insertion order of the keys.

### Functionalities

1. **Insertion**: Adds a key-value pair to the map.
   ```javascript
   let map = new Map();
   map.set(1, 'one');
   map.set(2, 'two');
   ```

2. **Deletion**: Removes a key-value pair from the map.
   ```javascript
   map.delete(1);
   ```

3. **Search**: Checks if a key is in the map.
   ```javascript
   if (map.has(2)) {
       console.log("Key 2 has value " + map.get(2));
   }
   ```

4. **Traversal**: Iterates through all key-value pairs in insertion order.
   ```javascript
   for (let [key, value] of map) {
       console.log(`Key: ${key}, Value: ${value}`);
   }
   ```

### Time and Space Complexity

#### `Map`

- **Insertion**: O(1) - Uses a hash table to store elements, so insertion is constant time.
- **Deletion**: O(1) - Uses the hash table to locate and remove elements.
- **Search**: O(1) - Uses the hash table to quickly find elements.
- **Space Complexity**: O(n) - Proportional to the number of elements, plus overhead for the hash table structure.

### Example

```javascript
let map = new Map();
map.set(1, 'one');
map.set(2, 'two');
map.set(3, 'three');

console.log("Map elements in insertion order:");
for (let [key, value] of map) {
    console.log(`Key: ${key}, Value: ${value}`);
}
```

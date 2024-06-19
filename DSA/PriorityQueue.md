
# Priority Queues

## What is a Priority Queue?

A **priority queue** is an abstract data type similar to a regular queue or stack data structure in which each element is associated with a "priority". In a priority queue, an element with high priority is served before an element with low priority. If two elements have the same priority, they are served according to their order in the queue.

### Key Characteristics:
1. **Order by Priority:** Elements are dequeued in order of their priority, not just their insertion order.
2. **Dynamic:** Priority can be assigned and changed dynamically.

## Implementation of Priority Queue

### C++ Implementation

In C++, the Standard Template Library (STL) provides a `priority_queue` class template which is part of the `<queue>` header. By default, it acts as a max-heap, where the largest element has the highest priority.

#### Example Code:

```cpp
#include <iostream>
#include <queue>
#include <vector>

int main() {
    // Create a max-heap priority queue
    std::priority_queue<int> pq;

    // Insert elements into the priority queue
    pq.push(10);
    pq.push(30);
    pq.push(20);
    pq.push(5);

    // Display and remove elements from the priority queue
    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

#### Functions Available:

- **push(element):** Inserts an element into the priority queue.
- **pop():** Removes the element with the highest priority.
- **top():** Returns the element with the highest priority without removing it.
- **empty():** Checks if the priority queue is empty.
- **size():** Returns the number of elements in the priority queue.

### Custom Comparator:

To implement a min-heap, you can use a custom comparator.

```cpp
#include <iostream>
#include <queue>
#include <vector>

int main() {
    // Create a min-heap priority queue
    std::priority_queue<int, std::vector<int>, std::greater<int>> pq;

    // Insert elements into the priority queue
    pq.push(10);
    pq.push(30);
    pq.push(20);
    pq.push(5);

    // Display and remove elements from the priority queue
    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

### Java Implementation

In Java, the `PriorityQueue` class is provided in the `java.util` package. By default, it is implemented as a min-heap, where the smallest element has the highest priority.

#### Example Code:

```java
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) {
        // Create a min-heap priority queue
        PriorityQueue<Integer> pq = new PriorityQueue<>();

        // Insert elements into the priority queue
        pq.add(10);
        pq.add(30);
        pq.add(20);
        pq.add(5);

        // Display and remove elements from the priority queue
        while (!pq.isEmpty()) {
            System.out.print(pq.poll() + " ");
        }
    }
}
```

#### Functions Available:

- **add(element):** Inserts an element into the priority queue.
- **poll():** Removes the element with the highest priority.
- **peek():** Returns the element with the highest priority without removing it.
- **isEmpty():** Checks if the priority queue is empty.
- **size():** Returns the number of elements in the priority queue.



### Custom Comparator:

To implement a max-heap, you can use a custom comparator.

```java
import java.util.Collections;
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) {
        // Create a max-heap priority queue
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

        // Insert elements into the priority queue
        pq.add(10);
        pq.add(30);
        pq.add(20);
        pq.add(5);

        // Display and remove elements from the priority queue
        while (!pq.isEmpty()) {
            System.out.print(pq.poll() + " ");
        }
    }
}
```


# Priority Queue with Custom Comparator in Java

## Introduction

A `PriorityQueue` in Java is a special type of queue where elements are ordered based on their priority. By default, the elements are ordered according to their natural ordering or by a `Comparator` provided at queue construction time.

## Custom Comparator Example

### Structure Explanation

```java
PriorityQueue<Pair> heap = new PriorityQueue<Pair>((x, y) -> x.dist - y.dist);
```

This line of code creates a `PriorityQueue` of `Pair` objects with a custom comparator. The custom comparator defines the order of the elements in the queue based on the `dist` field of the `Pair` objects.


### Key Components

1. **PriorityQueue<Pair>:** 
   This creates a priority queue that will hold objects of type `Pair`.

2. **(x, y) -> x.dist - y.dist:**
   This is a lambda expression that defines the custom comparator. It compares two `Pair` objects (`x` and `y`) based on their `dist` fields. The comparator determines the order of the elements in the queue:
   - If `x.dist` is less than `y.dist`, `x` will be placed before `y`.
   - If `x.dist` is greater than `y.dist`, `x` will be placed after `y`.

### Example

Let's create a `Pair` class and use the priority queue.

```java
import java.util.PriorityQueue;

class Pair {
    int key;
    int dist;

    // Constructor
    public Pair(int key, int dist) {
        this.key = key;
        this.dist = dist;
    }
}

public class Main {
    public static void main(String[] args) {
        // Create a priority queue with a custom comparator
        PriorityQueue<Pair> heap = new PriorityQueue<>((x, y) -> x.dist - y.dist);

        // Add some pairs to the priority queue
        heap.add(new Pair(1, 30));
        heap.add(new Pair(2, 20));
        heap.add(new Pair(3, 10));

        // Remove and print pairs from the priority queue
        while (!heap.isEmpty()) {
            Pair pair = heap.poll();
            System.out.println("Key: " + pair.key + ", Distance: " + pair.dist);
        }
    }
}
```

### Output
```
Key: 3, Distance: 10
Key: 2, Distance: 20
Key: 1, Distance: 30
```

- The pairs are printed in the order of their `dist` values, from smallest to largest.



## Conclusion

Priority queues are versatile and efficient data structures for managing ordered elements. They are implemented as heaps (min-heap or max-heap) and have several functions to insert, access, and remove elements based on priority. The standard libraries in both C++ and Java provide robust implementations of priority queues, making them easy to use for various applications.


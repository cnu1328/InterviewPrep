
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

## Conclusion

Priority queues are versatile and efficient data structures for managing ordered elements. They are implemented as heaps (min-heap or max-heap) and have several functions to insert, access, and remove elements based on priority. The standard libraries in both C++ and Java provide robust implementations of priority queues, making them easy to use for various applications.


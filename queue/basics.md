## **1️⃣ What is a Queue?**

* A **queue** is a **linear data structure**.
* Follows **FIFO (First-In, First-Out)** principle.
* **First element added** will be the **first one to be removed**.

**Real-life example:**

* People waiting in a line at a ticket counter.

---

## **2️⃣ Basic Operations of a Queue**

| Operation              | Description                                    |
| ---------------------- | ---------------------------------------------- |
| `add()` / `offer()`    | Insert element at the **rear** of the queue    |
| `remove()` / `poll()`  | Remove element from the **front** of the queue |
| `peek()` / `element()` | View the **front element** without removing it |
| `isEmpty()`            | Check if the queue is empty                    |

---

## **3️⃣ Queue Implementation in Java**

Java provides **built-in Queue interface** and classes like **LinkedList** or **ArrayDeque**.

### **Example using LinkedList**

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueBasics {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();

        // Add elements
        queue.add(10);  // adds 10
        queue.add(20);  // adds 20
        queue.add(30);  // adds 30

        System.out.println("Queue: " + queue);

        // Peek front element
        System.out.println("Front element: " + queue.peek());

        // Remove element
        System.out.println("Removed element: " + queue.poll());

        // Queue after removal
        System.out.println("Queue after removal: " + queue);

        // Check if empty
        System.out.println("Is queue empty? " + queue.isEmpty());
    }
}
```

---

### **Output**

```
Queue: [10, 20, 30]
Front element: 10
Removed element: 10
Queue after removal: [20, 30]
Is queue empty? false
```

---

## **4️⃣ Notes**

1. `add()` vs `offer()` → Both insert, but `add()` throws exception if capacity is full (for bounded queues), `offer()` returns false.
2. `remove()` vs `poll()` → `remove()` throws exception if empty, `poll()` returns null.
3. `peek()` vs `element()` → `peek()` returns null if empty, `element()` throws exception.

---

If you want, I can **draw a diagram showing how elements move in a queue**, then we can move on to **types of queues** like **circular, priority, and deque**.

Do you want me to do that next?

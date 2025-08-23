## 🌟 What is a Queue?

* A **Queue** is a **linear data structure** that follows the **FIFO (First In, First Out)** principle.
* Think of it like a line of people waiting at a ticket counter:

  * The person who enters first is served first.
  * New people join at the **rear (end)**.
  * Service is done from the **front (start)**.

---

## 🌟 Basic Queue Operations

1. **Enqueue (add)** → Add element to the rear.
2. **Dequeue (remove)** → Remove element from the front.
3. **Peek/Front** → Get the element at the front without removing it.
4. **isEmpty** → Check if the queue is empty.
5. **isFull** (for fixed-size array) → Check if the queue is full.

---

## 🌟 Ways to Implement Queue

1. **Using Array**
2. **Using Linked List**
3. **Using Java’s Built-in `Queue` interface**

---

## ✅ 1. Queue using Array

```java
class QueueArray {
    int arr[];
    int front, rear, size, capacity;

    public QueueArray(int capacity) {
        this.capacity = capacity;
        arr = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    // Enqueue
    void enqueue(int data) {
        if (size == capacity) {
            System.out.println("Queue is Full!");
            return;
        }
        rear = (rear + 1) % capacity;
        arr[rear] = data;
        size++;
    }

    // Dequeue
    int dequeue() {
        if (size == 0) {
            System.out.println("Queue is Empty!");
            return -1;
        }
        int val = arr[front];
        front = (front + 1) % capacity;
        size--;
        return val;
    }

    // Peek
    int peek() {
        if (size == 0) return -1;
        return arr[front];
    }

    boolean isEmpty() {
        return size == 0;
    }
}

public class Main {
    public static void main(String[] args) {
        QueueArray q = new QueueArray(5);
        q.enqueue(10);
        q.enqueue(20);
        q.enqueue(30);
        System.out.println("Front: " + q.peek());
        System.out.println("Removed: " + q.dequeue());
        System.out.println("Front after dequeue: " + q.peek());
    }
}
```

---

## ✅ 2. Queue using Linked List

```java
class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class QueueLL {
    Node front, rear;

    void enqueue(int data) {
        Node newNode = new Node(data);
        if (rear == null) {
            front = rear = newNode;
            return;
        }
        rear.next = newNode;
        rear = newNode;
    }

    int dequeue() {
        if (front == null) {
            System.out.println("Queue Empty!");
            return -1;
        }
        int val = front.data;
        front = front.next;
        if (front == null) rear = null;
        return val;
    }

    int peek() {
        if (front == null) return -1;
        return front.data;
    }

    boolean isEmpty() {
        return front == null;
    }
}

public class Main {
    public static void main(String[] args) {
        QueueLL q = new QueueLL();
        q.enqueue(5);
        q.enqueue(15);
        q.enqueue(25);
        System.out.println("Front: " + q.peek());
        System.out.println("Removed: " + q.dequeue());
        System.out.println("Front after dequeue: " + q.peek());
    }
}
```

---

## ✅ 3. Queue using Java’s `Queue` Interface

Java already provides `Queue` (implemented by `LinkedList` and `PriorityQueue`).

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Queue<Integer> q = new LinkedList<>();

        q.add(10);   // enqueue
        q.add(20);
        q.add(30);

        System.out.println("Front: " + q.peek());  // front element
        System.out.println("Removed: " + q.remove()); // dequeue
        System.out.println("Front after dequeue: " + q.peek());
        // Poll (alternative to remove but doesn’t throw exception when empty)
        System.out.println("Removed using poll: " + q.poll());
        // Clear queue
        q.clear();
    }
}
```

---

## 🌟 Types of Queues

1. **Simple Queue** (FIFO, like above)
2. **Circular Queue** (array queue with wrap-around indexing)
3. **Double-Ended Queue (Deque)** → insertion & deletion from both ends
4. **Priority Queue** → elements served based on priority, not arrival time

---

👉 Swathi, would you like me to next **draw step-by-step dry runs** of these queue operations (enqueue, dequeue) so you can *visualize* how elements move inside?

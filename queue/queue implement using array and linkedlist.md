Perfect 👍 Let’s write both implementations one by one.

---

## 1️⃣ Queue Implementation using **Array**

```java
class QueueArray {
    private int front, rear, size, capacity;
    private int[] arr;

    // Constructor
    public QueueArray(int capacity) {
        this.capacity = capacity;
        this.front = 0;
        this.size = 0;
        this.rear = capacity - 1;  // rear starts at last index
        this.arr = new int[capacity];
    }

    // Check if queue is full
    public boolean isFull() {
        return size == capacity;
    }

    // Check if queue is empty
    public boolean isEmpty() {
        return size == 0;
    }

    // Enqueue operation
    public void enqueue(int item) {
        if (isFull()) {
            System.out.println("Queue is full. Cannot enqueue " + item);
            return;
        }
        rear = (rear + 1) % capacity;  // circular increment
        arr[rear] = item;
        size++;
        System.out.println(item + " enqueued to queue");
    }

    // Dequeue operation
    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty. Cannot dequeue");
            return -1;
        }
        int item = arr[front];
        front = (front + 1) % capacity;  // circular increment
        size--;
        return item;
    }

    // Peek front element
    public int front() {
        if (isEmpty()) return -1;
        return arr[front];
    }

    // Peek rear element
    public int rear() {
        if (isEmpty()) return -1;
        return arr[rear];
    }

    // Display queue
    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is empty.");
            return;
        }
        System.out.print("Queue: ");
        for (int i = 0; i < size; i++) {
            System.out.print(arr[(front + i) % capacity] + " ");
        }
        System.out.println();
    }
}

// Testing
public class Main {
    public static void main(String[] args) {
        QueueArray q = new QueueArray(5);
        q.enqueue(10);
        q.enqueue(20);
        q.enqueue(30);
        q.enqueue(40);
        q.display();

        System.out.println("Dequeued: " + q.dequeue());
        q.display();

        System.out.println("Front: " + q.front());
        System.out.println("Rear: " + q.rear());
    }
}
```

✅ **Time Complexity:**

* Enqueue → `O(1)`
* Dequeue → `O(1)`
* Display → `O(n)`

---

## 2️⃣ Queue Implementation using **Linked List**

```java
class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class QueueLinkedList {
    private Node front, rear;

    public QueueLinkedList() {
        this.front = this.rear = null;
    }

    // Enqueue
    public void enqueue(int item) {
        Node newNode = new Node(item);
        if (rear == null) {
            front = rear = newNode;
            System.out.println(item + " enqueued to queue");
            return;
        }
        rear.next = newNode;
        rear = newNode;
        System.out.println(item + " enqueued to queue");
    }

    // Dequeue
    public int dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. Cannot dequeue");
            return -1;
        }
        int item = front.data;
        front = front.next;
        if (front == null) rear = null; // If queue becomes empty
        return item;
    }

    // Peek Front
    public int front() {
        if (front == null) return -1;
        return front.data;
    }

    // Peek Rear
    public int rear() {
        if (rear == null) return -1;
        return rear.data;
    }

    // Display
    public void display() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        System.out.print("Queue: ");
        Node temp = front;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }
}

// Testing
public class Main {
    public static void main(String[] args) {
        QueueLinkedList q = new QueueLinkedList();
        q.enqueue(10);
        q.enqueue(20);
        q.enqueue(30);
        q.enqueue(40);
        q.display();

        System.out.println("Dequeued: " + q.dequeue());
        q.display();

        System.out.println("Front: " + q.front());
        System.out.println("Rear: " + q.rear());
    }
}
```

✅ **Time Complexity:**

* Enqueue → `O(1)`
* Dequeue → `O(1)`
* Display → `O(n)`

---

Would you like me to **dry run both codes with input** (say, `10, 20, 30, 40` enqueue → then dequeue one) so you clearly see how array and linked list queues behave?

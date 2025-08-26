Perfect 👍 Let’s move to **Circular Queue** — it’s an important interview concept since it efficiently utilizes memory (no wastage like in linear queue).

---

## 🔹 Circular Queue

* A **queue** is *First In First Out (FIFO)*.
* In a **linear queue**, once the rear reaches the end, you cannot insert more elements even if there is space at the front.
* **Circular Queue** solves this problem by connecting the end of the array back to the front (like a circle).

👉 Operations: `enqueue()`, `dequeue()`, `isFull()`, `isEmpty()`, `peek()`

---

### ✅ Code: Circular Queue Using Array (Java)

```java
public class CircularQueue {
    private int[] queue;
    private int front, rear, size, capacity;

    // Constructor
    public CircularQueue(int capacity) {
        this.capacity = capacity;
        queue = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    // Enqueue
    public void enqueue(int value) {
        if (isFull()) {
            System.out.println("Queue is Full! Cannot insert " + value);
            return;
        }
        rear = (rear + 1) % capacity; // circular increment
        queue[rear] = value;
        size++;
    }

    // Dequeue
    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is Empty!");
            return -1;
        }
        int item = queue[front];
        front = (front + 1) % capacity; // circular increment
        size--;
        return item;
    }

    // Peek
    public int peek() {
        if (isEmpty()) {
            System.out.println("Queue is Empty!");
            return -1;
        }
        return queue[front];
    }

    // Check if full
    public boolean isFull() {
        return size == capacity;
    }

    // Check if empty
    public boolean isEmpty() {
        return size == 0;
    }

    // Display
    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is Empty!");
            return;
        }
        System.out.print("Queue: ");
        for (int i = 0; i < size; i++) {
            System.out.print(queue[(front + i) % capacity] + " ");
        }
        System.out.println();
    }

    // Main function
    public static void main(String[] args) {
        CircularQueue cq = new CircularQueue(5);

        cq.enqueue(10);
        cq.enqueue(20);
        cq.enqueue(30);
        cq.enqueue(40);
        cq.enqueue(50);
        cq.display();

        System.out.println("Dequeued: " + cq.dequeue());
        System.out.println("Dequeued: " + cq.dequeue());
        cq.display();

        cq.enqueue(60);
        cq.enqueue(70);
        cq.display();
    }
}
```

---

### 📌 Output Example

```
Queue: 10 20 30 40 50
Dequeued: 10
Dequeued: 20
Queue: 30 40 50
Queue: 30 40 50 60 70
```

---

⚡ **Time Complexity**

* Enqueue: `O(1)`
* Dequeue: `O(1)`
* Peek: `O(1)`
* Space: `O(n)`

---

👉 Next, do you want me to cover **Circular Queue using Linked List** (another approach) or shall we jump to **Queue interview problems** (like Rotten Oranges, Sliding Window Max, etc.)?

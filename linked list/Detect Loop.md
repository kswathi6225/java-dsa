
## **1️⃣ Detect Loop using Hashing**

```java
// Detect loop in Linked List using Hashing
import java.util.HashSet;

public class DetectLoopHashing {

    static class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; this.next = null; }
    }

    static class LinkedList {
        Node head;

        public void addLast(int val) {
            Node newNode = new Node(val);
            if (head == null) {
                head = newNode;
                return;
            }
            Node temp = head;
            while (temp.next != null) temp = temp.next;
            temp.next = newNode;
        }

        // Detect loop using HashSet
        public boolean hasLoop() {
            HashSet<Node> set = new HashSet<>();
            Node temp = head;
            while (temp != null) {
                if (set.contains(temp)) return true; // loop detected
                set.add(temp);
                temp = temp.next;
            }
            return false; // no loop
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);
        ll.addLast(4);

        // create loop: 4 -> 2
        ll.head.next.next.next.next = ll.head.next;

        System.out.println("Loop detected? " + ll.hasLoop());
    }
}
```

**Time Complexity:** O(n)
**Space Complexity:** O(n) (for HashSet)

---

## **2️⃣ Detect Loop using Tortoise & Hare (Floyd’s Cycle Detection)**

```java
// Detect loop in Linked List using Tortoise & Hare
public class DetectLoopFloyd {

    static class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; this.next = null; }
    }

    static class LinkedList {
        Node head;

        public void addLast(int val) {
            Node newNode = new Node(val);
            if (head == null) {
                head = newNode;
                return;
            }
            Node temp = head;
            while (temp.next != null) temp = temp.next;
            temp.next = newNode;
        }

        // Detect loop using slow-fast pointers
        public boolean hasLoop() {
            Node slow = head;
            Node fast = head;

            while (fast != null && fast.next != null) {
                slow = slow.next;
                fast = fast.next.next;

                if (slow == fast) return true; // loop detected
            }

            return false; // no loop
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);
        ll.addLast(4);

        // create loop: 4 -> 2
        ll.head.next.next.next.next = ll.head.next;

        System.out.println("Loop detected? " + ll.hasLoop());
    }
}
```

**Time Complexity:** O(n)
**Space Complexity:** O(1) ✅ (no extra space)

---

### **Summary**

| Approach        | Time Complexity | Space Complexity |
| --------------- | --------------- | ---------------- |
| Hashing         | O(n)            | O(n)             |
| Tortoise & Hare | O(n)            | O(1)             |

* **Hashing** is easy to implement but uses extra memory.
* **Floyd’s cycle detection** is optimal in **both time and space**, commonly asked in interviews.

---

I can also **write the code to find the start of the loop using Floyd’s method**, which is often a follow-up interview question.

Do you want me to do that?

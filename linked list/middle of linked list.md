

## **1️⃣ Brute Force Approach**

```java
// Brute Force Approach to Find Middle of Linked List
public class BruteForceMiddle {

    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
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

        public void printAll() {
            Node temp = head;
            while (temp != null) {
                System.out.print(temp.data + "->");
                temp = temp.next;
            }
            System.out.println("null");
        }

        public Node findMiddle() {
            if (head == null) return null;

            // First pass: count nodes
            int count = 0;
            Node temp = head;
            while (temp != null) {
                count++;
                temp = temp.next;
            }

            // Second pass: move to middle node
            int midIndex = count / 2; // second middle if even
            temp = head;
            for (int i = 0; i < midIndex; i++) temp = temp.next;

            return temp;
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);
        ll.addLast(4);
        ll.addLast(5);

        System.out.print("Linked List: ");
        ll.printAll();

        Node middle = ll.findMiddle();
        System.out.println("Middle (Brute Force): " + (middle != null ? middle.data : "List is empty"));
    }
}
```

**Time Complexity:** O(n) + O(n) ≈ O(n)
**Space Complexity:** O(1)

---

## **2️⃣ Tortoise & Hare (Slow-Fast Pointers) Approach**

```java
// Tortoise & Hare Approach to Find Middle of Linked List
public class TortoiseHareMiddle {

    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
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

        public void printAll() {
            Node temp = head;
            while (temp != null) {
                System.out.print(temp.data + "->");
                temp = temp.next;
            }
            System.out.println("null");
        }

        public Node findMiddle() {
            if (head == null) return null;

            Node slow = head;
            Node fast = head;

            while (fast != null && fast.next != null) {
                slow = slow.next;       // move 1 step
                fast = fast.next.next;  // move 2 steps
            }

            return slow;
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);
        ll.addLast(4);
        ll.addLast(5);

        System.out.print("Linked List: ");
        ll.printAll();

        Node middle = ll.findMiddle();
        System.out.println("Middle (Tortoise & Hare): " + (middle != null ? middle.data : "List is empty"));
    }
}
```

**Time Complexity:** O(n) (only one traversal)
**Space Complexity:** O(1)

---

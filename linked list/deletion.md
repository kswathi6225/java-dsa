
# Linked List Deletion Operations in Java

```java
import java.util.*;

public class LinkedList {
    Node head; // head of list

    // Node class
    class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            next = null;
        }
    }

    // Add node at end
    public void add(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) {
            temp = temp.next;
        }
        temp.next = newNode;
    }

    // Print the linked list
    public void print() {
        if (head == null) {
            System.out.println("List is empty");
            return;
        }
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("null");
    }

    // Delete head node
    public void deleteHead() {
        if (head == null) return;
        head = head.next;
    }

    // Delete tail node
    public void deleteTail() {
        if (head == null) return;
        if (head.next == null) { // only one element
            head = null;
            return;
        }
        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }
        temp.next = null;
    }

    // Delete first occurrence of a key
    public void delete(int key) {
        if (head == null) return;
        if (head.data == key) {
            head = head.next;
            return;
        }
        Node prev = null, curr = head;
        while (curr != null && curr.data != key) {
            prev = curr;
            curr = curr.next;
        }
        if (curr == null) return; // not found
        prev.next = curr.next;
    }

    // Delete node at specific index (0-based)
    public void deleteAtIndex(int index) {
        if (head == null || index < 0) return;
        if (index == 0) {
            head = head.next;
            return;
        }
        Node temp = head;
        for (int i = 0; i < index - 1; i++) {
            if (temp.next == null) return; // index out of bounds
            temp = temp.next;
        }
        if (temp.next == null) return; // index out of bounds
        temp.next = temp.next.next;
    }

    // Get length of the list
    public int length() {
        int count = 0;
        Node temp = head;
        while (temp != null) {
            count++;
            temp = temp.next;
        }
        return count;
    }

    // Main method to test
    public static void main(String[] args) {
        LinkedList ll = new LinkedList();

        // Input
        ll.add(10);
        ll.add(20);
        ll.add(30);
        ll.add(40);
        ll.add(50);

        System.out.println("Original List:");
        ll.print();

        // Delete operations
        ll.deleteHead();
        System.out.println("After deleting head:");
        ll.print();

        ll.deleteTail();
        System.out.println("After deleting tail:");
        ll.print();

        ll.delete(30);
        System.out.println("After deleting value 30:");
        ll.print();

        ll.deleteAtIndex(1);
        System.out.println("After deleting at index 1:");
        ll.print();

        // Length
        System.out.println("Length of list: " + ll.length());
    }
}
````

---

### ✅ Input

The linked list elements added:

```
10 -> 20 -> 30 -> 40 -> 50
```

---

### ✅ Output

```
Original List:
10 -> 20 -> 30 -> 40 -> 50 -> null
After deleting head:
20 -> 30 -> 40 -> 50 -> null
After deleting tail:
20 -> 30 -> 40 -> null
After deleting value 30:
20 -> 40 -> null
After deleting at index 1:
20 -> null
Length of list: 1
```

---

### ⏱ Time Complexity

| Operation          | Time Complexity        |
| ------------------ | ---------------------- |
| `deleteHead()`     | O(1)                   |
| `deleteTail()`     | O(n)                   |
| `delete(int key)`  | O(n)                   |
| `deleteAtIndex(i)` | O(i) → O(n) worst case |
| `length()`         | O(n)                   |
| `print()`          | O(n)                   |

---

### 🧠 Space Complexity

* All deletion operations are **in-place**, so **O(1) extra space** is required.
* The linked list itself uses O(n) space for storing nodes.

---

If you want, I can also **draw a diagram showing what happens for each deletion** — head, tail, value, and index — which is very helpful for interviews.

Do you want me to do that?

Got it! Here’s the **Linked List code with all deletion methods only** (delete by value, delete head, delete tail, delete by index), plus print and length for testing:

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

    // Delete head node
    public void deleteHead() {
        if (head == null) {
            System.out.println("List is empty, nothing to delete");
            return;
        }
        head = head.next;
    }

    // Delete tail node
    public void deleteTail() {
        if (head == null) {
            System.out.println("List is empty, nothing to delete");
            return;
        }
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

        if (curr == null) {
            System.out.println("Element " + key + " not found");
            return;
        }

        prev.next = curr.next;
    }

    // Delete by index (0-based)
    public void deleteAtIndex(int index) {
        if (head == null || index < 0) {
            System.out.println("Invalid operation");
            return;
        }

        if (index == 0) {
            head = head.next;
            return;
        }

        Node temp = head;
        for (int i = 0; i < index - 1; i++) {
            if (temp.next == null) {
                System.out.println("Index out of bounds");
                return;
            }
            temp = temp.next;
        }

        if (temp.next == null) {
            System.out.println("Index out of bounds");
            return;
        }

        temp.next = temp.next.next;
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

        // Adding elements manually
        ll.add(10);
        ll.add(20);
        ll.add(30);
        ll.add(40);
        ll.add(50);

        System.out.println("Original List:");
        ll.print();

        // Delete head
        ll.deleteHead();
        System.out.println("After deleting head:");
        ll.print();

        // Delete tail
        ll.deleteTail();
        System.out.println("After deleting tail:");
        ll.print();

        // Delete by value
        ll.delete(30);
        System.out.println("After deleting value 30:");
        ll.print();

        // Delete by index
        ll.deleteAtIndex(1);
        System.out.println("After deleting at index 1:");
        ll.print();
    }

    // Add at end helper
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
}
```

---

### ✅ Features in this code:

* `deleteHead()` → removes the first node
* `deleteTail()` → removes the last node
* `delete(int key)` → removes the **first occurrence** of a value
* `deleteAtIndex(int index)` → removes node at a **specific index**
* `print()` → shows the list
* `length()` → returns number of nodes

---

If you want, I can also **draw a diagram showing head, tail, and how each deletion works visually**, which makes it super easy to understand.

Do you want me to do that?

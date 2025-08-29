1. Insert at end
2. Insert at beginning
3. Insert at a given position
4. Delete by value
5. Delete by position
6. Reverse the DLL
7. Display forward and backward

This will cover almost all **interview questions** on DLL.

---

# 🟢 Complete Doubly Linked List in Java

```java
import java.util.*;

class Node {
    int data;
    Node next;
    Node prev;

    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    Node head;

    // 1️⃣ Insert at end
    void insertEnd(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) temp = temp.next;
        temp.next = newNode;
        newNode.prev = temp;
    }

    // 2️⃣ Insert at beginning
    void insertBeginning(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        newNode.next = head;
        head.prev = newNode;
        head = newNode;
    }

    // 3️⃣ Insert at a given position (1-based)
    void insertAtPosition(int data, int pos) {
        if (pos == 1) {
            insertBeginning(data);
            return;
        }
        Node newNode = new Node(data);
        Node temp = head;
        for (int i = 1; i < pos - 1 && temp != null; i++) temp = temp.next;

        if (temp == null) {
            System.out.println("Position out of bounds");
            return;
        }

        newNode.next = temp.next;
        if (temp.next != null) temp.next.prev = newNode;
        temp.next = newNode;
        newNode.prev = temp;
    }

    // 4️⃣ Delete by value
    void deleteByValue(int key) {
        Node temp = head;
        if (temp == null) return;

        if (temp.data == key) { // delete head
            head = temp.next;
            if (head != null) head.prev = null;
            return;
        }

        while (temp != null && temp.data != key) temp = temp.next;
        if (temp == null) return;

        if (temp.next != null) temp.next.prev = temp.prev;
        if (temp.prev != null) temp.prev.next = temp.next;
    }

    // 5️⃣ Delete by position (1-based)
    void deleteByPosition(int pos) {
        if (head == null) return;
        Node temp = head;

        if (pos == 1) {
            head = temp.next;
            if (head != null) head.prev = null;
            return;
        }

        for (int i = 1; i < pos && temp != null; i++) temp = temp.next;
        if (temp == null) return;

        if (temp.next != null) temp.next.prev = temp.prev;
        if (temp.prev != null) temp.prev.next = temp.next;
    }

    // 6️⃣ Reverse DLL
    void reverse() {
        Node temp = null;
        Node current = head;

        while (current != null) {
            temp = current.prev;
            current.prev = current.next;
            current.next = temp;
            current = current.prev;
        }

        if (temp != null) head = temp.prev;
    }

    // 7️⃣ Display forward
    void displayForward() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.next;
        }
        System.out.println("NULL");
    }

    // 8️⃣ Display backward
    void displayBackward() {
        Node temp = head;
        if (temp == null) return;

        while (temp.next != null) temp = temp.next; // go to last
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.prev;
        }
        System.out.println("NULL");
    }

    // Main method to test
    public static void main(String[] args) {
        DoublyLinkedList dll = new DoublyLinkedList();

        // Insert
        dll.insertEnd(10);
        dll.insertEnd(20);
        dll.insertEnd(30);
        dll.insertBeginning(5);
        dll.insertAtPosition(15, 3); // Insert 15 at 3rd position

        System.out.println("DLL Forward:");
        dll.displayForward();

        System.out.println("DLL Backward:");
        dll.displayBackward();

        // Delete
        dll.deleteByValue(20);
        System.out.println("After deleting 20:");
        dll.displayForward();

        dll.deleteByPosition(2);
        System.out.println("After deleting at position 2:");
        dll.displayForward();

        // Reverse
        dll.reverse();
        System.out.println("After reversing DLL:");
        dll.displayForward();
    }
}
```

---

### **Sample Input/Operations**

```
Insert End: 10, 20, 30
Insert Beginning: 5
Insert at Position 3: 15
Delete by Value: 20
Delete by Position: 2
Reverse DLL
```

### **Sample Output**

```
DLL Forward:
5 <-> 10 <-> 15 <-> 20 <-> 30 <-> NULL
DLL Backward:
30 <-> 20 <-> 15 <-> 10 <-> 5 <-> NULL
After deleting 20:
5 <-> 10 <-> 15 <-> 30 <-> NULL
After deleting at position 2:
5 <-> 15 <-> 30 <-> NULL
After reversing DLL:
30 <-> 15 <-> 5 <-> NULL
```

---

### **Complexity Analysis**

| Operation           | Time | Space |
| ------------------- | ---- | ----- |
| Insert at end       | O(n) | O(1)  |
| Insert at beginning | O(1) | O(1)  |
| Insert at position  | O(n) | O(1)  |
| Delete by value     | O(n) | O(1)  |
| Delete by position  | O(n) | O(1)  |
| Reverse DLL         | O(n) | O(1)  |
| Display             | O(n) | O(1)  |

---

If you want, I can also **draw a diagram showing DLL structure and pointers** for all operations — it helps visualize for interviews.

Do you want me to do that?

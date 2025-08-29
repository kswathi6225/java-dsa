# 🟢 **Doubly Linked List (DLL) – Introduction**

A **Doubly Linked List** is a data structure where each node contains:

1. **Data** – The value stored in the node.
2. **Next Pointer** – Points to the next node in the list.
3. **Previous Pointer** – Points to the previous node in the list.

**Advantages over Singly Linked List:**

* Can traverse **forward and backward**.
* Easier to **delete a node** if you have a pointer to it.

**Node Representation in Java:**

```java
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
```

---

# 🔹 1️⃣ Insert a Node in DLL (at end)

### **Java Code**

```java
class DoublyLinkedList {
    Node head;

    // Insert at end
    void insert(int data) {
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
        newNode.prev = temp;
    }

    // Display list
    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.next;
        }
        System.out.println("NULL");
    }

    public static void main(String[] args) {
        DoublyLinkedList dll = new DoublyLinkedList();
        dll.insert(10);
        dll.insert(20);
        dll.insert(30);
        dll.display();
    }
}
```

### **Input**

```
Insert 10, 20, 30
```

### **Output**

```
10 <-> 20 <-> 30 <-> NULL
```

### **Complexity**

* **Time:** `O(n)` (traverse to end)
* **Space:** `O(1)` extra

---

# 🔹 2️⃣ Delete a Node in DLL (by value)

### **Java Code**

```java
class DoublyLinkedListDelete {
    Node head;

    void insert(int data) {
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

    void delete(int key) {
        Node temp = head;

        // Empty list
        if (temp == null) return;

        // Deleting head
        if (temp.data == key) {
            head = temp.next;
            if (head != null) head.prev = null;
            return;
        }

        while (temp != null && temp.data != key) {
            temp = temp.next;
        }

        if (temp == null) return; // Key not found

        // Bypass temp
        if (temp.next != null) temp.next.prev = temp.prev;
        if (temp.prev != null) temp.prev.next = temp.next;
    }

    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.next;
        }
        System.out.println("NULL");
    }

    public static void main(String[] args) {
        DoublyLinkedListDelete dll = new DoublyLinkedListDelete();
        dll.insert(10);
        dll.insert(20);
        dll.insert(30);
        dll.display();

        dll.delete(20);
        dll.display();
    }
}
```

### **Input**

```
Insert: 10, 20, 30
Delete: 20
```

### **Output**

```
10 <-> 20 <-> 30 <-> NULL
10 <-> 30 <-> NULL
```

### **Complexity**

* **Time:** `O(n)` (search for node)
* **Space:** `O(1)`

---

# 🔹 3️⃣ Reverse a DLL (Medium)

* Swap `next` and `prev` pointers of each node.
* Move `head` to last node after reversal.

### **Java Code**

```java
class DoublyLinkedListReverse {
    Node head;

    void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) { head = newNode; return; }
        Node temp = head;
        while (temp.next != null) temp = temp.next;
        temp.next = newNode;
        newNode.prev = temp;
    }

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

    void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " <-> ");
            temp = temp.next;
        }
        System.out.println("NULL");
    }

    public static void main(String[] args) {
        DoublyLinkedListReverse dll = new DoublyLinkedListReverse();
        dll.insert(10);
        dll.insert(20);
        dll.insert(30);
        dll.display();

        dll.reverse();
        dll.display();
    }
}
```

### **Input**

```
Insert: 10, 20, 30
Reverse DLL
```

### **Output**

```
10 <-> 20 <-> 30 <-> NULL
30 <-> 20 <-> 10 <-> NULL
```

### **Complexity**

* **Time:** `O(n)`
* **Space:** `O(1)`

---

# ✅ Summary

| Operation       | Time | Space |
| --------------- | ---- | ----- |
| Insert at end   | O(n) | O(1)  |
| Delete by value | O(n) | O(1)  |
| Reverse DLL     | O(n) | O(1)  |

---

If you want, I can also **show Insert at Beginning, Insert at Position, and Delete by Position** — those are **classic interview variations** for DLL.

Do you want me to do that next?

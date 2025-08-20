```java
public class Main {
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

        // Add element at the end
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

        // Find length of linked list
        public int length() {
            int count = 0;
            Node temp = head;
            while (temp != null) {
                count++;
                temp = temp.next;
            }
            return count;
        }

        public boolean search(int key) {
            Node temp = head;
            while (temp != null) {
                if (temp.data == key) return true;
                temp = temp.next;
            }
            return false;
        }

        // Print linked list
        public void printAll() {
            Node temp = head;
            while (temp != null) {
                System.out.print(temp.data + "->");
                temp = temp.next;
            }
            System.out.println("null");
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);

        System.out.print("Linked List: ");
        ll.printAll();

        int key2 = 5;

        System.out.println("Searching for " + key1 + ": " + ll.search(key1));

        System.out.println("Length of the list: " + ll.length());
    }
}
```

---

### **Output**

```
Linked List: 1->2->3->null
Length of the list: 3
```

---

### **Time Complexity**

| Operation  | Time Complexity |
| ---------- | --------------- |
| addLast()  | O(n) per call   |
| length()   | O(n)            |
| printAll() | O(n)            |

### **Space Complexity**

* O(1) → only uses a few pointers (`temp`, `count`).

---

If you want, I can **also modify this linked list to use a `tail` pointer**, so `addLast()` becomes **O(1)** instead of O(n).

Do you want me to do that?

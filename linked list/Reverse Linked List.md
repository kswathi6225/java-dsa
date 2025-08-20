
# Reverse Linked List in Java

## **Code**

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

        // Print linked list
        public void printAll() {
            Node temp = head;
            while (temp != null) {
                System.out.print(temp.data + "->");
                temp = temp.next;
            }
            System.out.println("null");
        }

        // Reverse the linked list
        public void reverse() {
            if (head == null || head.next == null) return;

            Node prevNode = head;
            Node currNode = head.next;
            Node nextNode;

            while (currNode != null) {
                nextNode = currNode.next;
                currNode.next = prevNode;

                // update pointers
                prevNode = currNode;
                currNode = nextNode;
            }

            head.next = null;
            head = prevNode;
        }
    }

    public static void main(String[] args) {
        LinkedList ll = new LinkedList();
        ll.addLast(1);
        ll.addLast(2);
        ll.addLast(3);

        System.out.print("Original List: ");
        ll.printAll();

        ll.reverse();

        System.out.print("Reversed List: ");
        ll.printAll();
    }
}
````

---

## **Input**

* Elements added to the linked list using `addLast` method:

```
1, 2, 3
```

---

## **Output**

```
Original List: 1->2->3->null
Reversed List: 3->2->1->null
```

---

## **Time and Space Complexity**

| Operation  | Time Complexity | Space Complexity |
| ---------- | --------------- | ---------------- |
| addLast()  | O(n) per call   | O(1)             |
| printAll() | O(n)            | O(1)             |
| reverse()  | O(n)            | O(1)             |

```

This markdown includes the **code**, **input**, **output**, and **complexity table**.
```


## **Idea**

* Use **two pointers**:

  * `slow` moves **one step** at a time.
  * `fast` moves **two steps** at a time.
* When `fast` reaches the end, `slow` will be at the **middle node**.

---

## **Code (Java)**

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

        // Find middle node
        public Node findMiddle() {
            if (head == null) return null;

            Node slow = head;
            Node fast = head;

            while (fast != null && fast.next != null) {
                slow = slow.next;
                fast = fast.next.next;
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
        System.out.println("Middle of the list: " + (middle != null ? middle.data : "List is empty"));
    }
}
```

---

## **Output**

```
Linked List: 1->2->3->4->5->null
Middle of the list: 3
```

---

### **Time and Space Complexity**

| Operation    | Time Complexity | Space Complexity |
| ------------ | --------------- | ---------------- |
| findMiddle() | O(n)            | O(1)             |

* `n` = number of nodes.
* Only one traversal is required.
* Constant extra space is used.

---

If you want, I can also show a **version that returns the second middle node** in case the list has **even number of nodes**, which is often required in some problems.

Do you want me to do that?

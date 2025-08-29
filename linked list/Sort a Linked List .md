Got it 👍
One of the most common interview questions is **sorting a linked list**. Since linked lists don’t support random access like arrays, efficient sorting is usually done using **Merge Sort**, which works in **O(n log n)** time.

Here’s the **Java code with input, output, time & space complexity** in Markdown:

---

## 📌 Sort a Linked List (Merge Sort)

```java
class LinkedList {
    Node head;

    static class Node {
        int data;
        Node next;
        Node(int d) {
            data = d;
            next = null;
        }
    }

    // Function to sort linked list
    public Node sortList(Node head) {
        if (head == null || head.next == null)
            return head;

        // Step 1: Split list into two halves
        Node middle = getMiddle(head);
        Node nextOfMiddle = middle.next;
        middle.next = null;

        // Step 2: Sort both halves
        Node left = sortList(head);
        Node right = sortList(nextOfMiddle);

        // Step 3: Merge sorted halves
        return merge(left, right);
    }

    // Utility function to merge two sorted lists
    Node merge(Node left, Node right) {
        if (left == null) return right;
        if (right == null) return left;

        Node result;
        if (left.data <= right.data) {
            result = left;
            result.next = merge(left.next, right);
        } else {
            result = right;
            result.next = merge(left, right.next);
        }
        return result;
    }

    // Utility function to get middle of list
    Node getMiddle(Node head) {
        if (head == null) return head;

        Node slow = head, fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    // Function to print the list
    void printList(Node node) {
        while (node != null) {
            System.out.print(node.data + " ");
            node = node.next;
        }
        System.out.println();
    }

    // Driver code
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.head = new Node(4);
        list.head.next = new Node(2);
        list.head.next.next = new Node(1);
        list.head.next.next.next = new Node(3);

        System.out.println("Original List:");
        list.printList(list.head);

        list.head = list.sortList(list.head);

        System.out.println("Sorted List:");
        list.printList(list.head);
    }
}
```

---

### ✅ Input:

```
Original List:
4 2 1 3
```

### ✅ Output:

```
Sorted List:
1 2 3 4
```

---

### ⏱️ Time Complexity:

* **O(n log n)** → Merge Sort recursion + merging of lists.

### 💾 Space Complexity:

* **O(log n)** → Recursion stack for merge sort (not using extra array).

---

Do you want me to also give **QuickSort on Linked List**? (It’s asked less often than merge sort, but sometimes comes up in interviews.)

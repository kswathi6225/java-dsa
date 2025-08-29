### 1️⃣ Merge Two Sorted Linked Lists

```java
// Merge Two Sorted Linked Lists
public class MergeSortedLL {

    static class Node {
        int data;
        Node next;
        Node(int d) { data = d; next = null; }
    }

    static Node merge(Node l1, Node l2) {
        Node dummy = new Node(0);
        Node tail = dummy;

        while (l1 != null && l2 != null) {
            if (l1.data < l2.data) {
                tail.next = l1;
                l1 = l1.next;
            } else {
                tail.next = l2;
                l2 = l2.next;
            }
            tail = tail.next;
        }

        // attach remaining nodes
        if (l1 != null) tail.next = l1;
        if (l2 != null) tail.next = l2;

        return dummy.next;
    }

    static void printList(Node head) {
        while (head != null) {
            System.out.print(head.data + " -> ");
            head = head.next;
        }
        System.out.println("null");
    }

    public static void main(String[] args) {
        Node l1 = new Node(1);
        l1.next = new Node(3);
        l1.next.next = new Node(5);

        Node l2 = new Node(2);
        l2.next = new Node(4);
        l2.next.next = new Node(6);

        Node merged = merge(l1, l2);
        printList(merged);
    }
}
```

✅ **Input:**

```
List1: 1 -> 3 -> 5
List2: 2 -> 4 -> 6
```

✅ **Output:**

```
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> null
```

⏱ **Time Complexity:** O(n + m)
💾 **Space Complexity:** O(1) (in-place, ignoring recursion stack)

---

so give you **Union & Intersection of Two Unsorted Linked Lists** (not intersection point, but new list)? That’s another fav placement twist.

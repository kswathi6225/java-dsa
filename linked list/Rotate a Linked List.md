
**Rotate a Linked List** is one of the *very common* interview questions. Let’s go step by step.

---

## 📝 Problem Statement

Rotate a linked list to the right by `k` places.

### Example

```
Input: 1 -> 2 -> 3 -> 4 -> 5, k = 2  
Output: 4 -> 5 -> 1 -> 2 -> 3
```

---

## 💡 Key Idea

1. Find length of list.
2. Connect the last node to head (make it circular).
3. Move `(len - k % len)` steps to find new head.
4. Break the circle.

---

## ✅ Code (Java)

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class RotateList {
    public static ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) return head;

        // Step 1: Find length and tail
        ListNode curr = head;
        int len = 1;
        while (curr.next != null) {
            curr = curr.next;
            len++;
        }
        ListNode tail = curr;

        // Step 2: Make it circular
        tail.next = head;

        // Step 3: Find new head position
        k = k % len;
        int stepsToNewHead = len - k;
        ListNode newTail = tail;

        while (stepsToNewHead-- > 0) {
            newTail = newTail.next;
        }

        // Step 4: Break the circle
        ListNode newHead = newTail.next;
        newTail.next = null;

        return newHead;
    }

    // Helper to print list
    public static void printList(ListNode head) {
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Example: 1->2->3->4->5, k=2
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        System.out.print("Original List: ");
        printList(head);

        head = rotateRight(head, 2);

        System.out.print("Rotated List: ");
        printList(head);
    }
}
```

---

## 📊 Complexity

* **Time:** O(n) (one pass for length + one pass for rotation)
* **Space:** O(1) (in-place)

---


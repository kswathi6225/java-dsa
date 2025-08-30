## 📝 Problem Statement

Remove the **N-th node from the end** of a singly linked list.

### Example

```
Input: 1 -> 2 -> 3 -> 4 -> 5, n = 2
Output: 1 -> 2 -> 3 -> 5
```

(Removed the 2nd node from the end, which is 4.)

---

## 💡 Approach

We use **two-pointer technique (fast and slow)**:

1. Move `fast` pointer `n` steps ahead.
2. Move both `slow` and `fast` until `fast.next == null`.
3. `slow.next` is the node to remove. Update `slow.next = slow.next.next`.

---

## ✅ Code (Java)

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class RemoveNthFromEnd {

    public static ListNode removeNthFromEnd(ListNode head, int n) {
        // Dummy node to handle edge case: removing head
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode slow = dummy;
        ListNode fast = dummy;

        // Move fast n+1 steps ahead
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }

        // Move slow and fast together
        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }

        // Delete the N-th node from end
        slow.next = slow.next.next;

        return dummy.next;
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
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        System.out.print("Original List: ");
        printList(head);

        head = removeNthFromEnd(head, 2);

        System.out.print("After Removing 2nd Node from End: ");
        printList(head);
    }
}
```

---

## 📊 Complexity

* **Time:** O(n) → traverse the list once
* **Space:** O(1) → in-place, no extra space

---

Do you want me to also **draw a dry run table** like we did for the intersection and rotation? It helps to understand the two-pointer technique visually.

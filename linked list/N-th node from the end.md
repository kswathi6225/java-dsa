https://www.geeksforgeeks.org/dsa/nth-node-from-the-end-of-a-linked-list/
refer this too i is to return the nth node only 
----

## 📝 Problem Statement

Remove the **N-th node from the end** of a singly linked list.

### Example

```
Input: 1 -> 2 -> 3 -> 4 -> 5, n = 2
Output: 1 -> 2 -> 3 -> 5
```

(Removed the 2nd node from the end, which is 4.)

---

## 💡 Approaches

### 1️⃣ Brute Force

1. Traverse the linked list to calculate its **length** `len`.
2. Calculate the **position from the start**: `pos = len - n`.
3. Traverse again to the `(pos-1)`-th node and update its `next` pointer to skip the N-th node from the end.

**Time Complexity:** O(2n) → two traversals
**Space Complexity:** O(1) → in-place

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class RemoveNthFromEndBrute {

    public static ListNode removeNthFromEnd(ListNode head, int n) {
        int len = 0;
        ListNode temp = head;
        while (temp != null) {
            len++;
            temp = temp.next;
        }

        // If we need to remove the head
        if (n == len) {
            return head.next;
        }

        temp = head;
        for (int i = 1; i < len - n; i++) {
            temp = temp.next;
        }
        temp.next = temp.next.next;
        return head;
    }

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

        System.out.print("After Removing 2nd Node from End (Brute): ");
        printList(head);
    }
}
```

---

### 2️⃣ Optimized Approach: Two Pointers (Fast & Slow)

1. Use a **dummy node** pointing to head to handle edge cases (like removing the first node).
2. Move the `fast` pointer `n + 1` steps ahead.
3. Move `slow` and `fast` together until `fast` reaches the end.
4. `slow.next` is the node to remove; skip it by `slow.next = slow.next.next`.

**Time Complexity:** O(n) → single traversal
**Space Complexity:** O(1) → in-place

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class RemoveNthFromEnd {

    public static ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode slow = dummy;
        ListNode fast = dummy;

        // Move fast n+1 steps ahead
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }
        if(fast== null) return head.next; //EDGE CASE: the first node should be deleted
        // Move slow and fast together
        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }

        // Delete the N-th node from end
        slow.next = slow.next.next;

        return dummy.next;
    }

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

        System.out.print("After Removing 2nd Node from End (Two Pointers): ");
        printList(head);
    }
}
```

---

## 📊 Dry Run Table (Two Pointers)

| Step | `slow` | `fast` | Action                                             |
| ---- | ------ | ------ | -------------------------------------------------- |
| 0    | dummy  | dummy  | Initialize dummy node before head                  |
| 1    | dummy  | 1      | Move fast 1 step (i=0)                             |
| 2    | dummy  | 2      | Move fast 2 steps (i=1)                            |
| 3    | dummy  | 3      | Move fast 3 steps (i=2)                            |
| 4    | dummy  | 4      | Move fast 4 steps (i=3)                            |
| 5    | dummy  | 5      | Move fast 5 steps (i=4)                            |
| 6    | dummy  | null   | Move fast 6 steps (i=5), end reached               |
| 7    | 3      | null   | Move slow & fast together until fast null          |
| 8    | 3      | null   | Skip node: slow\.next = slow\.next.next → remove 4 |

**Resulting List:** `1 -> 2 -> 3 -> 5`

---



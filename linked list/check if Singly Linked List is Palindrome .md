Got it 👍 Let’s write **Palindrome Check in a Linked List**.
I’ll give you **different approaches**, their **Java code**, **time & space complexity**, and **example input/output** in **Markdown format**.

---

# Palindrome Check in Linked List

## Approach 1: Using Extra Space (Stack / ArrayList)

* Store all node values in a list/stack.
* Compare front and back values.

### Code

```java
import java.util.*;

public class PalindromeLL {
    static class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; }
    }

    // Check palindrome using extra space
    public static boolean isPalindrome(Node head) {
        ArrayList<Integer> list = new ArrayList<>();
        Node temp = head;
        while (temp != null) {
            list.add(temp.data);
            temp = temp.next;
        }
        int left = 0, right = list.size() - 1;
        while (left < right) {
            if (!list.get(left).equals(list.get(right))) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(2);
        head.next.next.next = new Node(1);

        System.out.println(isPalindrome(head)); // true
    }
}
```

### Complexity

* **Time:** O(n)
* **Space:** O(n) (extra array/stack storage)

---

## Approach 2: Reverse Second Half

* Find middle of LL (slow & fast pointer).
* Reverse second half.
* Compare first half & reversed half.
* Restore if needed.

### Code

```java
public class PalindromeLL2 {
    static class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; }
    }

    // Reverse helper
    private static Node reverse(Node head) {
        Node prev = null, curr = head, next = null;
        while (curr != null) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }

    // Check palindrome
    public static boolean isPalindrome(Node head) {
        if (head == null || head.next == null) return true;

        // Find middle (slow will stop at mid)
        Node slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse second half
        Node secondHalf = reverse(slow);
        Node copySecond = secondHalf; // keep to restore later

        // Compare halves
        Node firstHalf = head;
        while (secondHalf != null) {
            if (firstHalf.data != secondHalf.data) {
                return false;
            }
            firstHalf = firstHalf.next;
            secondHalf = secondHalf.next;
        }

        // Optional: Restore list (reverse again)
        reverse(copySecond);

        return true;
    }

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(2);
        head.next.next.next = new Node(1);

        System.out.println(isPalindrome(head)); // true
    }
}
```

### Complexity

* **Time:** O(n)
* **Space:** O(1) (no extra array used)

---


✅ Best Approach for Interviews: **Approach 2 (Reverse Second Half)** since it’s **O(n) time & O(1) space**.

---

Do you want me to also add a **dry run example diagram** (step by step) for the reverse-second-half method? That will help in interviews.

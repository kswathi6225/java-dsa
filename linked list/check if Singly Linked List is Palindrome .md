## ✅ Code: Check if Singly Linked List is Palindrome (Java)

```java
// Palindrome Check in Singly Linked List
class PalindromeSLL {
    static class Node {
        int data;
        Node next;
        Node(int d) {
            data = d;
            next = null;
        }
    }

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
    }

    // Reverse linked list
    Node reverse(Node head) {
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
    boolean isPalindrome() {
        if (head == null || head.next == null) return true;

        // Step 1: Find middle using slow & fast pointer
        Node slow = head, fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Step 2: Reverse second half
        slow.next = reverse(slow.next);

        // Step 3: Compare first and second half
        Node p1 = head, p2 = slow.next;
        while (p2 != null) {
            if (p1.data != p2.data) return false;
            p1 = p1.next;
            p2 = p2.next;
        }

        return true;
    }

    // Print list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        PalindromeSLL list = new PalindromeSLL();
        list.insert(1);
        list.insert(2);
        list.insert(3);
        list.insert(2);
        list.insert(1);

        System.out.print("Linked List: ");
        list.printList();

        if (list.isPalindrome())
            System.out.println("Palindrome ✅");
        else
            System.out.println("Not Palindrome ❌");
    }
}
```

---

## 📌 Input & Output

### Input

```
1 -> 2 -> 3 -> 2 -> 1
```

### Output

```
Linked List: 1 2 3 2 1 
Palindrome ✅
```

### Another Input

```
1 -> 2 -> 3 -> 4
```

### Output

```
Linked List: 1 2 3 4
Not Palindrome ❌
```

---

## ⏱️ Time & Space Complexity

* **Time Complexity**: `O(n)`

  * Finding middle → `O(n/2)`
  * Reversing half → `O(n/2)`
  * Comparing halves → `O(n/2)`
  * ✅ Overall: `O(n)`
* **Space Complexity**: `O(1)` (in-place reversal, no extra space)

---

👉 Do you also want me to give the **brute force approach (using stack or array)** for palindrome in SLL, so you can compare?

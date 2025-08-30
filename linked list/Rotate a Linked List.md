# Rotate Linked List

## Node Definition
```java
class Node {
    int data;
    Node next;
    Node(int data) { this.data = data; }
}
````

---

## Left Rotation by `k` nodes

```java
class LinkedList {

    static Node rotateLeft(Node head, int k) {
        if (head == null || k == 0) return head;

        Node curr = head;
        int len = 1;

        // find the length of linked list
        while (curr.next != null) {
            curr = curr.next;
            len++;
        }

        k %= len;
        if (k == 0) return head;

        // make circular
        curr.next = head;

        // move to kth node
        curr = head;
        for (int i = 1; i < k; i++) curr = curr.next;

        // new head is (k+1)th node
        head = curr.next;

        // break the loop
        curr.next = null;

        return head;
    }
}
```

---

## Right Rotation by `k` nodes

```java
class LinkedList {

    static Node rotateRight(Node head, int k) {
        if (head == null || k == 0) return head;

        Node curr = head;
        int len = 1;

        // find length
        while (curr.next != null) {
            curr = curr.next;
            len++;
        }

        // right rotation is same as left rotation by (len - k)
        k = k % len;
        if (k == 0) return head;

        int leftRotate = len - k;

        // make circular
        curr.next = head;

        // move to (leftRotate)th node
        curr = head;
        for (int i = 1; i < leftRotate; i++) curr = curr.next;

        // new head
        head = curr.next;
        curr.next = null;

        return head;
    }
}
```

---

## Print Function

```java
static void printList(Node head) {
    Node temp = head;
    while (temp != null) {
        System.out.print(temp.data);
        if(temp.next != null) System.out.print(" -> ");
        temp = temp.next;
    }
    System.out.println();
}
```

---

## Input & Output Example

```java
public static void main(String[] args) {
    Node head = new Node(10);
    head.next = new Node(20);
    head.next.next = new Node(30);
    head.next.next.next = new Node(40);

    // Left rotation by 2
    head = rotateLeft(head, 2);
    printList(head); // Output: 30 -> 40 -> 10 -> 20

    // Reset list
    head = new Node(10);
    head.next = new Node(20);
    head.next.next = new Node(30);
    head.next.next.next = new Node(40);

    // Right rotation by 1
    head = rotateRight(head, 1);
    printList(head); // Output: 40 -> 10 -> 20 -> 30
}
```

---

## Time Complexity

* Finding length: O(n)
* Moving to rotation point: O(n)
* Overall: **O(n)**

## Space Complexity

* Only pointer variables used: **O(1)**

---

## Notes / Changes

1. Right rotation is equivalent to **left rotation by `(len - k)`** nodes.
2. Circular link trick (`curr.next = head`) simplifies both left and right rotations.
3. Handles cases where `k > length` using modulo (`k %= len`).

```

---

If you want, I can also **draw a step-by-step dry run table for both left and right rotation** so it’s crystal clear how nodes move.  

Do you want me to do that next?
```

# Rotate Linked List
--
## Explanation if u want is at last
--
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
        for (int i = 1; i < leftRotate; i++) curr = curr.next;  //only difference b/w both is len-k

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


```

Perfect! Let’s do a **complete, detailed dry run** of your `rotateLeft` function **step by step** for the input:

**Input:** `10 -> 20 -> 30 -> 40`, `k = 2`

---

### **Step 0: Initial setup**

```java
Node curr = head;   // curr points to 10
int len = 1;        // length counter starts at 1
```

* `head` points to `10 -> 20 -> 30 -> 40`
* `curr` is also at `10`
* `len = 1`

---

### **Step 1: Calculate length of list**

```java
while (curr.next != null) {
    curr = curr.next;
    len++;
}
```

| Iteration | curr.data | len |
| --------- | --------- | --- |
| 1         | 20        | 2   |
| 2         | 30        | 3   |
| 3         | 40        | 4   |

* Loop ends because `curr.next == null`
* **Length = 4**, `curr` points to `40` (last node)

---

### **Step 2: Adjust k**

```java
k %= len;  // k = 2 % 4 = 2
if (k == 0) return head;
```

* `k = 2`
* Not 0, so we continue

---

### **Step 3: Make list circular**

```java
curr.next = head;  // 40 -> 10
```

* Current list visually (circular now):

```
10 -> 20 -> 30 -> 40
^                   |
|___________________|
```

* `curr` still points to `40`

---

### **Step 4: Move to k-th node**

```java
curr = head;
for (int i = 1; i < k; i++) curr = curr.next;
```

| i | curr.data |                                                            |
| - | --------- | ---------------------------------------------------------- |
| 1 | 10        |                                                            |
| 2 | 20        | ✅ stop, now curr points to 2nd node (node before new head) |

---

### **Step 5: Update head**

```java
head = curr.next; // head = 30
```

* `head` now points to `30 -> 40 -> 10 -> 20 -> ... (circular for now)`

---

### **Step 6: Break the loop**

```java
curr.next = null; // 20.next = null
```

* Circular link is broken
* Final rotated list:

```
30 -> 40 -> 10 -> 20 -> null
```

---

### ✅ **Step 7: Return**

* Function returns `head` pointing to `30`
* Output: `30 -> 40 -> 10 -> 20`

---



### 2️⃣ Intersection Point of Two Linked Lists
---
## Just learn two pointers its enough
--------------
## ✅ Approaches to Solve

### **1. Brute Force (Nested Loops)**

* For each node in list A, traverse the entire list B and check if any node matches by reference.
* **Code idea:**

  ```java
  for (Node a = headA; a != null; a = a.next) {
      for (Node b = headB; b != null; b = b.next) {
          if (a == b) return a;
      }
  }
  return null;
  ```
* **Time Complexity:** O(m \* n)
* **Space Complexity:** O(1)
* **Drawback:** Very slow for large lists.

---

### **2. Hashing**

* Traverse one list (say A) and store all nodes in a `HashSet`.
* Then traverse list B and check if any node exists in the set.
* **Code idea:**

  ```java
  HashSet<Node> set = new HashSet<>();
  for (Node a = headA; a != null; a = a.next) {
      set.add(a);
  }
  for (Node b = headB; b != null; b = b.next) {
      if (set.contains(b)) return b;
  }
  return null;
  ```
* **Time Complexity:** O(m + n)
* **Space Complexity:** O(m) or O(n)

---

### **3. Length Difference Method**

* Count lengths of both lists.
* Move the pointer of the longer list ahead by `|lenA - lenB|` nodes so both pointers have the same number of nodes left.
* Then traverse both simultaneously until they meet.
* **Code idea:**

  ```java
  static int getLength(Node head) {
      int len = 0;
      while (head != null) { len++; head = head.next; }
      return len;
  }

  static Node getIntersection(Node headA, Node headB) {
      int lenA = getLength(headA);
      int lenB = getLength(headB);

      while (lenA > lenB) { headA = headA.next; lenA--; }
      while (lenB > lenA) { headB = headB.next; lenB--; }

      while (headA != headB) {
          headA = headA.next;
          headB = headB.next;
      }
      return headA;
  }
  ```
* **Time Complexity:** O(m + n)
* **Space Complexity:** O(1)

---

### **4. Two Pointer Approach (Most Efficient)**

* Use two pointers `a` and `b`.
* Traverse each list. When a pointer reaches the end, switch it to the head of the other list.
* If the lists intersect, the pointers will eventually meet at the intersection node.
* If not, both will reach `null`.
* **Why this works?**
  Both pointers cover equal distance `m + n` in total. If they intersect, they meet at the intersection node.
* **Code (your given one):**

  ```java
  static Node getIntersection(Node headA, Node headB) {
      if (headA == null || headB == null) return null;
      Node a = headA, b = headB;
      while (a != b) {
          a = (a == null) ? headB : a.next;
          b = (b == null) ? headA : b.next;
      }
      return a;
  }
  ```
* **Time Complexity:** O(m + n)
* **Space Complexity:** O(1)
* **Best Approach ✅**

---

## 🔥 Conclusion

* **Brute Force** → Worst, O(m\*n).
* **Hashing** → Faster but uses extra space.
* **Length Difference** → Good, O(m+n), O(1) space.
* **Two Pointer** → Best, O(m+n), O(1) space, very elegant.

---

```java
// Intersection Point of Two Linked Lists
public class IntersectionLL {

    static class Node {
        int data;
        Node next;
        Node(int d) { data = d; next = null; }
    }

    // Find intersection using 2 pointer approach
    static Node getIntersection(Node headA, Node headB) {
        if (headA == null || headB == null) return null;

        Node a = headA;
        Node b = headB;

        while (a != b) {
            a = (a == null) ? headB : a.next;
            b = (b == null) ? headA : b.next;
        }

        return a; // either intersection node or null
    }

    public static void main(String[] args) {
        // Common part
        Node common = new Node(8);
        common.next = new Node(10);

        // List A: 3 -> 7 -> 8 -> 10
        Node headA = new Node(3);
        headA.next = new Node(7);
        headA.next.next = common;

        // List B: 99 -> 1 -> 8 -> 10
        Node headB = new Node(99);
        headB.next = new Node(1);
        headB.next.next = common;

        Node intersection = getIntersection(headA, headB);
        if (intersection != null)
            System.out.println("Intersection at node: " + intersection.data);
        else
            System.out.println("No intersection");
    }
}
```

✅ **Input:**

```
List A: 3 -> 7 -> 8 -> 10
List B: 99 -> 1 -> 8 -> 10
```

✅ **Output:**

```
Intersection at node: 8
```

⏱ **Time Complexity:** O(n + m)
💾 **Space Complexity:** O(1)

---

Do you want me to al

### 2️⃣ Intersection Point of Two Linked Lists

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

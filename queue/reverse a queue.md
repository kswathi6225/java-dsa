## ✅ Approach 1: Using Stack (Iterative)

We use a stack as a helper because stack reverses order (LIFO).

```java
import java.util.*;

public class ReverseQueueStack {
    public static void reverseQueue(Queue<Integer> q) {
        Stack<Integer> stack = new Stack<>();

        // Step 1: Move all elements from Queue to Stack
        while (!q.isEmpty()) {
            stack.push(q.remove());
        }

        // Step 2: Push them back from Stack to Queue (reverses order)
        while (!stack.isEmpty()) {
            q.add(stack.pop());
        }
    }

    public static void main(String[] args) {
        Queue<Integer> q = new LinkedList<>();
        q.add(1);
        q.add(2);
        q.add(3);
        q.add(4);
        q.add(5);

        System.out.println("Original Queue: " + q);
        reverseQueue(q);
        System.out.println("Reversed Queue: " + q);
    }
}
```

**Output:**

```
Original Queue: [1, 2, 3, 4, 5]
Reversed Queue: [5, 4, 3, 2, 1]
```

---

## ✅ Approach 2: Using Recursion

Here, recursion itself acts like a stack.

```java
import java.util.*;

public class ReverseQueueRecursion {
    public static void reverseQueue(Queue<Integer> q) {
        if (q.isEmpty()) return;

        int front = q.remove();   // take one element
        reverseQueue(q);          // reverse remaining
        q.add(front);             // add element at the end
    }

    public static void main(String[] args) {
        Queue<Integer> q = new LinkedList<>();
        q.add(1);
        q.add(2);
        q.add(3);
        q.add(4);
        q.add(5);

        System.out.println("Original Queue: " + q);
        reverseQueue(q);
        System.out.println("Reversed Queue: " + q);
    }
}
```

**Output:**

```
Original Queue: [1, 2, 3, 4, 5]
Reversed Queue: [5, 4, 3, 2, 1]
```

---

🔥 **Interview Tip:**

* **Stack method** → Easy, iterative, O(n) time, O(n) space.
* **Recursion method** → Elegant, O(n) time, but recursion uses O(n) call stack space.

---

Do you want me to also give you a **variation problem** (like reverse *first K elements* of a queue)? This is another **very frequently asked** interview question.

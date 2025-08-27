## first 2 approaches enough

---

## 🔹 Problem Statement:

An element is called a **Leader** if it is **greater than or equal to all the elements to its right**.
The rightmost element is always a leader.

👉 Example:

```
Input: [16, 17, 4, 3, 5, 2]
Output: [17, 5, 2]
```

Explanation:

* 2 is a leader (last element).
* 5 is greater than 2 → leader.
* 3 is not greater than 5.
* 4 is not greater than 5.
* 17 is greater than all to its right → leader.
* 16 is not greater than 17.

---

## 🔹 Approach 1: Brute Force (O(n²))

Check each element by comparing it with all elements to its right.

```java
import java.util.*;

public class LeadersInArray {
    public static void main(String[] args) {
        int arr[] = {16, 17, 4, 3, 5, 2};
        int n = arr.length;

        System.out.print("Leaders: ");
        for (int i = 0; i < n; i++) {
            boolean isLeader = true;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > arr[i]) {
                    isLeader = false;
                    break;
                }
            }
            if (isLeader) {
                System.out.print(arr[i] + " ");
            }
        }
    }
}
```

✅ Output:

```
Leaders: 17 5 2
```

---

## 🔹 Approach 2: Optimal (O(n)) – Traverse from Right

Instead of checking every time, we traverse from right and keep track of the **current maximum**.

```java
import java.util.*;

public class LeadersInArray {
    public static void main(String[] args) {
        int arr[] = {16, 17, 4, 3, 5, 2};
        int n = arr.length;
        
        List<Integer> leaders = new ArrayList<>();
        int maxRight = arr[n - 1];
        leaders.add(maxRight);  // last element always leader

        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] >= maxRight) {
                leaders.add(arr[i]);
                maxRight = arr[i];
            }
        }

        // Reverse list to maintain left-to-right order
        Collections.reverse(leaders);

        System.out.println("Leaders: " + leaders);
    }
}
```

✅ Output:

```
Leaders: [17, 5, 2]
```

---

## 🔹 Approach 3: Stack Method (O(n))

We can also push leaders into a stack while traversing from right.

```java
import java.util.*;

public class LeadersInArray {
    public static void main(String[] args) {
        int arr[] = {16, 17, 4, 3, 5, 2};
        int n = arr.length;

        Stack<Integer> st = new Stack<>();
        int maxRight = arr[n - 1];
        st.push(maxRight);

        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] >= maxRight) {
                st.push(arr[i]);
                maxRight = arr[i];
            }
        }

        System.out.print("Leaders: ");
        while (!st.isEmpty()) {
            System.out.print(st.pop() + " ");
        }
    }
}
```

✅ Output:

```
Leaders: 17 5 2
```

---

📌 **Summary of Complexities:**

* Brute Force → **O(n²)**
* Optimal (Right-to-Left) → **O(n)**
* Stack Method → **O(n)**

---

👉 Do you want me to also draw a **step-by-step dry run** (like showing what `maxRight` stores at each step) for the **Optimal Approach**?

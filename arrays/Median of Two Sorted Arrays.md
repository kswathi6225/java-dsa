# 📘 Median of Two Sorted Arrays

We are given two **sorted arrays**.
We need to find the **median** of the combined sorted array **without merging unnecessarily**.

---

## 1️⃣ Brute Force (Merge Completely)

### 💡 Idea

* Merge both arrays into one sorted array.
* Return the middle element(s) depending on odd/even length.

### 📝 Code

```java
import java.util.*;

public class MedianArrays {
    public static double medianBrute(int[] a, int[] b) {
        int n1 = a.length, n2 = b.length;
        List<Integer> merged = new ArrayList<>();

        int i = 0, j = 0;
        while (i < n1 && j < n2) {
            if (a[i] < b[j]) merged.add(a[i++]);
            else merged.add(b[j++]);
        }
        while (i < n1) merged.add(a[i++]);
        while (j < n2) merged.add(b[j++]);

        int n = n1 + n2;
        if (n % 2 == 1) return merged.get(n / 2);
        return (merged.get(n / 2 - 1) + merged.get(n / 2)) / 2.0;
    }

    public static void main(String[] args) {
        int[] a = {1, 4, 7, 10, 12};
        int[] b = {2, 3, 6, 15};
        System.out.println("Median = " + medianBrute(a, b)); // 6.0
    }
}
```

### ⏱ Complexity

* **Time:** `O(n1 + n2)`
* **Space:** `O(n1 + n2)`

---

## 2️⃣ Better (Two-Pointer Without Full Merge)

### 💡 Idea

* Perform merge **only until the middle index**.
* Keep track of median candidates directly.

### 📝 Code

```java
public class MedianArrays {
    public static double medianBetter(int[] a, int[] b) {
        int n1 = a.length, n2 = b.length;
        int total = n1 + n2;
        int mid2 = total / 2, mid1 = mid2 - 1;

        int i = 0, j = 0, count = 0;
        int m1 = -1, m2 = -1;

        while (i < n1 && j < n2) {
            int val = (a[i] < b[j]) ? a[i++] : b[j++];
            if (count == mid1) m1 = val;
            if (count == mid2) m2 = val;
            count++;
        }

        while (i < n1) {
            int val = a[i++];
            if (count == mid1) m1 = val;
            if (count == mid2) m2 = val;
            count++;
        }

        while (j < n2) {
            int val = b[j++];
            if (count == mid1) m1 = val;
            if (count == mid2) m2 = val;
            count++;
        }

        if (total % 2 == 1) return m2;
        return (m1 + m2) / 2.0;
    }

    public static void main(String[] args) {
        int[] a = {1, 4, 7, 10, 12};
        int[] b = {2, 3, 6, 15};
        System.out.println("Median = " + medianBetter(a, b)); // 6.0
    }
}
```

### ⏱ Complexity

* **Time:** `O(n1 + n2)` (but stops early, so slightly faster)
* **Space:** `O(1)`

---

## 3️⃣ Optimal (Binary Search Partition)

### 💡 Idea

* Use **binary search** on the smaller array.
* Partition arrays into **left** and **right halves** such that:
  `max(leftA, leftB) <= min(rightA, rightB)`
* Median depends on whether total length is odd/even.

### 📝 Code

```java
public class MedianArrays {
    public static double medianOptimal(int[] a, int[] b) {
        if (a.length > b.length) return medianOptimal(b, a); // ensure a is smaller

        int n1 = a.length, n2 = b.length;
        int total = n1 + n2;
        int half = (total + 1) / 2;

        int low = 0, high = n1;
        while (low <= high) {
            int cut1 = (low + high) / 2;
            int cut2 = half - cut1;

            int leftA = (cut1 == 0) ? Integer.MIN_VALUE : a[cut1 - 1];
            int leftB = (cut2 == 0) ? Integer.MIN_VALUE : b[cut2 - 1];
            int rightA = (cut1 == n1) ? Integer.MAX_VALUE : a[cut1];
            int rightB = (cut2 == n2) ? Integer.MAX_VALUE : b[cut2];

            if (leftA <= rightB && leftB <= rightA) {
                if (total % 2 == 0) {
                    return (Math.max(leftA, leftB) + Math.min(rightA, rightB)) / 2.0;
                } else {
                    return Math.max(leftA, leftB);
                }
            } else if (leftA > rightB) {
                high = cut1 - 1;
            } else {
                low = cut1 + 1;
            }
        }
        return 0; // dummy
    }

    public static void main(String[] args) {
        int[] a = {1, 4, 7, 10, 12};
        int[] b = {2, 3, 6, 15};
        System.out.println("Median = " + medianOptimal(a, b)); // 6.0
    }
}
```

### ⏱ Complexity

* **Time:** `O(log(min(n1, n2)))`
* **Space:** `O(1)`

---

## 📊 Summary Table

| Approach                | Time Complexity       | Space Complexity | Notes                    |
| ----------------------- | --------------------- | ---------------- | ------------------------ |
| Brute Force (Merge)     | `O(n1 + n2)`          | `O(n1 + n2)`     | Easiest but heavy memory |
| Better (Two Pointers)   | `O(n1 + n2)`          | `O(1)`           | Lighter, no full merge   |
| Optimal (Binary Search) | `O(log(min(n1, n2)))` | `O(1)`           | Best for interviews      |

---

✅ Example Input / Output

```
Input: a = [1, 4, 7, 10, 12], b = [2, 3, 6, 15]
Output: 6.0

Input: a = [1, 3], b = [2]
Output: 2.0

Input: a = [1, 2], b = [3, 4]
Output: 2.5
```

---

Would you like me to also **draw the partition step dry run** for the binary search method (with `a=[1,3]`, `b=[2]`) so you clearly see how the left/right halves are decided?


# 🪣 Container With Most Water – Java Solutions

## Problem Statement

Given an array `arr[]` of non-negative integers, where each element `arr[i]` represents the height of the vertical lines,
find the **maximum amount of water** that can be contained between any two lines along with the x-axis.

---

## **Approach 1 – Naive (Brute Force)**

**Idea:**
Check **all possible pairs** of lines `(i, j)` and calculate water = `min(arr[i], arr[j]) * (j - i)`.
Keep track of the maximum water found.

**Time Complexity:** `O(n²)`
**Space Complexity:** `O(1)`

```java
public class ContainerBruteForce {
    static int maxWater(int[] arr) {
        int n = arr.length;
        int res = 0;

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int water = Math.min(arr[i], arr[j]) * (j - i);
                res = Math.max(res, water);
            }
        }

        return res;
    }

    public static void main(String[] args) {
        int[] arr = {2, 1, 8, 6, 4, 6, 5, 5};
        System.out.println("Max Water (Brute Force): " + maxWater(arr)); // Output: 25
    }
}
```

---

## **Approach 2 – Two Pointers (Optimized)**

**Idea:**

* Use two pointers: one at the start (`left`) and one at the end (`right`).
* Calculate the water between them.
* Move the pointer that points to the **shorter line**, since moving the taller line won’t help increase height but will reduce width.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

```java
public class ContainerTwoPointer {
    static int maxWater(int[] arr) {
        int left = 0, right = arr.length - 1;
        int res = 0;

        while (left < right) {
            int water = Math.min(arr[left], arr[right]) * (right - left);
            res = Math.max(res, water);

            if (arr[left] < arr[right]) {
                left++;
            } else {
                right--;
            }
        }

        return res;
    }

    public static void main(String[] args) {
        int[] arr = {2, 1, 8, 6, 4, 6, 5, 5};
        System.out.println("Max Water (Two Pointers): " + maxWater(arr)); // Output: 25
    }
}
```

---

✅ **Recommendation:** Always use the **Two Pointer** method for this problem—it’s much faster than brute force.

---

Do you want me to also **draw a visual diagram** in the Markdown so the container logic becomes intuitive? That would make it easier to remember.

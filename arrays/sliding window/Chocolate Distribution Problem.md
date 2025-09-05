Ah nice one 👍 The **Chocolate Distribution Problem** is another very popular interview question, often asked in Amazon, Microsoft, TCS, Infosys, etc.

Let’s break it down step by step 👇

---

# 🔹 Problem Statement

Given:

* An array `arr[]` of size `n`, where each element represents the number of chocolates in a packet.
* An integer `m` → the number of students.

Task:
Distribute packets among `m` students **such that**:

* Each student gets **exactly one packet**.
* The **difference between the maximum chocolates and minimum chocolates** among chosen packets is **minimum**.

---

# 🔹 Example

**Input:**

```
arr = [7, 3, 2, 4, 9, 12, 56]
m = 3
```

**Output:**

```
2
```

**Explanation:**

* If we distribute `[2, 3, 4]` → max = 4, min = 2 → difference = 2 ✅
* Any other choice gives a bigger difference.

---

# 🔹 Approach

👉 Idea:

1. **Sort the array.**
2. Consider **every subarray of length m**.
3. Find difference = `arr[i+m-1] - arr[i]`.
4. Return the **minimum** among all.

---

# 🔹 Complexity

* Sorting: `O(n log n)`
* Traversal: `O(n)`
* **Total:** `O(n log n)`
* **Space:** `O(1)`

---

# ✅ Java Code

```java
import java.util.Arrays;

public class ChocolateDistribution {

    public static int findMinDiff(int[] arr, int m) {
        int n = arr.length;
        if (m == 0 || n == 0) return 0;
        if (m > n) return -1; // Not enough packets

        // Sort the packets
        Arrays.sort(arr);

        int minDiff = Integer.MAX_VALUE;

        // Traverse subarrays of size m
        for (int i = 0; i + m - 1 < n; i++) {
            int diff = arr[i + m - 1] - arr[i];
            minDiff = Math.min(minDiff, diff);
        }

        return minDiff;
    }

    public static void main(String[] args) {
        int[] arr = {7, 3, 2, 4, 9, 12, 56};
        int m = 3;
        System.out.println("Minimum difference = " + findMinDiff(arr, m));
    }
}
```

---

# 🔹 Output

**Input:**

```
arr = [7, 3, 2, 4, 9, 12, 56], m = 3
```

**Output:**

```
Minimum difference = 2
```

---

# 🔹 Dry Run

Sorted array: `[2, 3, 4, 7, 9, 12, 56]`

* Subarray `[2,3,4] → diff = 2` ✅
* Subarray `[3,4,7] → diff = 4`
* Subarray `[4,7,9] → diff = 5`
* Subarray `[7,9,12] → diff = 5`
* Subarray `[9,12,56] → diff = 47`

👉 Minimum = **2**

---

# 🔹 Summary

* **Topic:** Sorting + Sliding Window
* **Best Approach:** Sort & take minimum difference among consecutive windows of size `m`.
* **Time Complexity:** `O(n log n)`
* **Space Complexity:** `O(1)`

---

👉 Bro, do you want me to also give you the **Naive O(n·m) approach** (checking all combinations without sorting) so you know the difference for interviews?

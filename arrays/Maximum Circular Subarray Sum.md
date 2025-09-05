# 🔹 Problem: Maximum Circular Subarray Sum

You are given an array of integers.
Find the **maximum sum of a subarray**, where the subarray can be **circular** (wraps around from the end of the array to the beginning).

---

## 🔹 Example

**Input:**

```
arr = [8, -1, 3, 4]
```

**Output:**

```
15
```

**Explanation:**

* Normal max subarray (Kadane): `8 + (-1) + 3 + 4 = 14`
* Circular case: `[3, 4, 8] = 15` ✅

---

# 🔹 Approach 1: Naive (Brute Force)

👉 Idea:

* Consider every element as a starting point.
* Traverse `n` elements forward (use modulo for circular wrap).
* Track maximum sum.

⏱️ **Time Complexity:** `O(n²)`
💾 **Space Complexity:** `O(1)`

---

### ✅ Java Code (Naive)

```java
public class MaxCircularSubarrayNaive {

    public static int maxCircularSum(int[] arr) {
        int n = arr.length;
        int res = arr[0];

        // Pick every starting point
        for (int i = 0; i < n; i++) {
            int currSum = arr[i];
            int currMax = arr[i];

            // Try all subarrays starting at i
            for (int j = 1; j < n; j++) {
                int index = (i + j) % n; // wrap around
                currSum += arr[index];
                currMax = Math.max(currMax, currSum);
            }

            res = Math.max(res, currMax);
        }

        return res;
    }

    public static void main(String[] args) {
        int[] arr = {8, -1, 3, 4};
        System.out.println("Naive Result = " + maxCircularSum(arr)); // 15
    }
}
```

---

# 🔹 Approach 2: Optimal (Kadane’s + Wrapping)

👉 Idea:

* Case 1: Maximum sum in **normal subarray** (Kadane’s).
* Case 2: Maximum sum in **circular subarray** = `totalSum - minSubarraySum`.
* Answer = `max(case1, case2)`.
* Edge Case: If all numbers are negative → return `maxNormal`.

⏱️ **Time Complexity:** `O(n)`
💾 **Space Complexity:** `O(1)`

---

### ✅ Java Code (Optimal)

```java
public class MaxCircularSubarrayOptimal {

    // Kadane’s Algorithm: Max subarray sum
    public static int kadane(int[] arr) {
        int maxEndingHere = arr[0];
        int maxSoFar = arr[0];

        for (int i = 1; i < arr.length; i++) {
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }
        return maxSoFar;
    }

    public static int maxCircularSubarraySum(int[] arr) {
        int n = arr.length;

        // Case 1: Normal Kadane
        int maxNormal = kadane(arr);

        // If all elements are negative
        if (maxNormal < 0) {
            return maxNormal;
        }

        // Case 2: Circular sum
        int totalSum = 0;
        for (int i = 0; i < n; i++) {
            totalSum += arr[i];
            arr[i] = -arr[i]; // invert array for min subarray
        }

        int maxCircular = totalSum + kadane(arr); // because -minSubarray = kadane(inverted)

        return Math.max(maxNormal, maxCircular);
    }

    public static void main(String[] args) {
        int[] arr = {8, -1, 3, 4};
        System.out.println("Optimal Result = " + maxCircularSubarraySum(arr)); // 15
    }
}
```

---

# 🔹 Dry Run Example

Input: `[8, -1, 3, 4]`

1. **Kadane’s Normal**:

   * max sum = `14` (`[8, -1, 3, 4]`).

2. **Circular Case**:

   * Total sum = `14`.
   * Min subarray = `[-1]`.
   * Circular sum = `14 - (-1) = 15`.

👉 Answer = `max(14, 15) = 15`. ✅

---

# 🔹 Summary

| Approach                    | Time    | Space  | Notes                                    |
| --------------------------- | ------- | ------ | ---------------------------------------- |
| Naive (Brute Force)         | `O(n²)` | `O(1)` | Try all subarrays (wrap with modulo).    |
| Optimal (Kadane + Wrapping) | `O(n)`  | `O(1)` | Best for interviews. Handles edge cases. |

---

👉 Bro, do you also want me to include the **all negative numbers case** dry run? (That’s a common interview twist).

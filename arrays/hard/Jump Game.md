Nice pick 🚀 “**Jump Game – Minimum Jumps to Reach End**” is a very popular interview problem.
Let’s go step by step from basics → brute force → greedy optimal.

---

# 🔹 Problem Statement

Given an array `arr[]` of size `n`, where each element represents the **maximum steps** that can be taken forward from that element.

Find the **minimum number of jumps** required to reach the last element of the array (starting from index 0).

If it’s not possible to reach the end, return `-1`.

---

# 🔹 Example

**Input:**

```
arr = [1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9]
```

**Output:**

```
3
```

**Explanation:**

* Jump 1 → from `1` → reach index `1`
* Jump 2 → from `3` → reach index `3`
* Jump 3 → from `8` → reach end

---

# 🔹 Approaches

---

## ✅ Approach 1: Naive (Recursive / DP)

Try all paths using recursion → pick the minimum.
⚠️ Very slow for large arrays.

* **Time Complexity:** `O(2^n)` (exponential, worst case).
* **Space Complexity:** `O(n)` (stack depth).

---

### Java Code (Naive DP with Memoization)

```java
public class JumpGameNaive {

    static int minJumpsRec(int[] arr, int n) {
        // If already at last element
        if (n == 1) return 0;

        int res = Integer.MAX_VALUE;

        // Check from all previous positions
        for (int i = 0; i <= n - 2; i++) {
            if (i + arr[i] >= n - 1) {
                int subRes = minJumpsRec(arr, i + 1);
                if (subRes != Integer.MAX_VALUE) {
                    res = Math.min(res, subRes + 1);
                }
            }
        }
        return res;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9};
        int n = arr.length;
        int result = minJumpsRec(arr, n);
        System.out.println("Naive Result = " + result); // 3
    }
}
```

---

## ✅ Approach 2: Greedy (Optimal)

👉 Idea:

* Track **farthest** reachable index so far.
* Track **end** of current jump range.
* Increase **jumps** when you cross the current range.

This is like a **level-order BFS traversal** of array ranges.

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

---

### Java Code (Greedy Optimal)

```java
public class JumpGameOptimal {

    public static int minJumps(int[] arr) {
        int n = arr.length;

        // Base cases
        if (n <= 1) return 0;          // already at end
        if (arr[0] == 0) return -1;    // cannot move

        int jumps = 1;     // at least one jump needed
        int maxReach = arr[0];
        int steps = arr[0];

        for (int i = 1; i < n; i++) {
            // Reached end
            if (i == n - 1) return jumps;

            // Update max reach
            maxReach = Math.max(maxReach, i + arr[i]);

            steps--;

            // If no more steps left → must take jump
            if (steps == 0) {
                jumps++;
                if (i >= maxReach) return -1; // cannot move further
                steps = maxReach - i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9};
        System.out.println("Optimal Result = " + minJumps(arr)); // 3
    }
}
```

---

# 🔹 Dry Run (Greedy)

Input: `[1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9]`

* Start → jumps=1, maxReach=1, steps=1
* i=1 → maxReach=4, steps=0 → jump++ (2), steps=3
* i=2 → maxReach=7
* i=3 → maxReach=11
* i=4 → maxReach=13, steps=0 → jump++ (3), steps=9
* Reached end ✅ Answer=3

---

# 🔹 Summary

| Approach           | Time     | Space  | Notes                                    |
| ------------------ | -------- | ------ | ---------------------------------------- |
| Naive Recursion/DP | `O(2^n)` | `O(n)` | Tries all paths, impractical for large n |
| Greedy Optimal     | `O(n)`   | `O(1)` | Best approach, used in interviews        |

---

👉 Bro, do you want me to also show the **DP tabulation approach** (O(n²)) that’s sometimes taught between naive and greedy?

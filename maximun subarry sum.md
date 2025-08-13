
# Maximum Subarray Sum Problem

**Problem:**
Given an integer array, find the contiguous subarray with the largest sum and return that sum.

---

## 1. Brute Force Approach (O(n³))

* Generate all possible subarrays.
* Calculate the sum of each subarray.
* Keep track of the maximum sum found.

```java
public class MaxSubarraySum {

    public static int maxSubArrayBruteForce(int[] nums) {
        int maxSum = Integer.MIN_VALUE;
        int n = nums.length;

        for (int start = 0; start < n; start++) {
            for (int end = start; end < n; end++) {
                int currentSum = 0;
                for (int k = start; k <= end; k++) {
                    currentSum += nums[k];
                }
                if (currentSum > maxSum) {
                    maxSum = currentSum;
                }
            }
        }
        return maxSum;
    }

    public static void main(String[] args) {
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Max subarray sum (Brute Force): " + maxSubArrayBruteForce(nums));
    }
}
```

---

## 2. Improved Brute Force with Prefix Sum (O(n²))

* Avoid recalculating sums repeatedly.
* Precompute sums or accumulate while iterating.

```java
public class MaxSubarraySum {

    public static int maxSubArrayPrefixSum(int[] nums) {
        int maxSum = Integer.MIN_VALUE;
        int n = nums.length;

        for (int start = 0; start < n; start++) {
            int currentSum = 0;
            for (int end = start; end < n; end++) {
                currentSum += nums[end];
                if (currentSum > maxSum) {
                    maxSum = currentSum;
                }
            }
        }
        return maxSum;
    }

    public static void main(String[] args) {
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Max subarray sum (Prefix Sum): " + maxSubArrayPrefixSum(nums));
    }
}
```

---

## 3. Kadane’s Algorithm — Optimized (O(n))

* Iterate once over the array.
* Keep track of:

  * Maximum subarray sum ending at current index (`currentSum`)
  * Global maximum sum found so far (`maxSum`)
* Reset current sum to 0 if it becomes negative.

```java
public class MaxSubarraySum {

    public static int maxSubArrayKadane(int[] nums) {
        int maxSum = nums[0];
        int currentSum = 0;

        for (int num : nums) {
            currentSum += num;

            if (currentSum > maxSum) {
                maxSum = currentSum;
            }

            if (currentSum < 0) {
                currentSum = 0;
            }
        }
        return maxSum;
    }

    public static void main(String[] args) {
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Max subarray sum (Kadane’s Algorithm): " + maxSubArrayKadane(nums));
    }
}
```

---

### Explanation of Kadane’s Algorithm:

* `currentSum` accumulates the sum of the current subarray.
* If `currentSum` drops below zero, reset it (start new subarray).
* `maxSum` stores the max sum seen so far.

---

### 🔹 Input

```
Enter size of array: 5
Enter 5 elements:
1 2 3 4 5
```

### 🔹 Output

```
Maximum subarray sum (Brute Force): 15
```

---

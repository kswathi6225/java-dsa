## Problem Statement

Given an array `arr[]` of size `n` and an integer `k`, find the length of the **longest subarray** whose sum is equal to `k`.

---

## 🔹Approach 1: Brute Force (O(n²))

Check all subarrays and calculate sum.

```java
// Brute Force: O(n^2)
public class LongestSubarraySumK {
    public static int longestSubarray(int[] arr, int k) {
        int n = arr.length;
        int maxLen = 0;

        for (int i = 0; i < n; i++) {
            int sum = 0;
            for (int j = i; j < n; j++) {
                sum += arr[j];
                if (sum == k) {
                    maxLen = Math.max(maxLen, j - i + 1);
                }
            }
        }
        return maxLen;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 1, 1, 1, 1};
        int k = 3;
        System.out.println("Longest Subarray Length = " + longestSubarray(arr, k));
    }
}
```

✅ Input: `arr = [1,2,3,1,1,1,1], k = 3`
✅ Output: `3` (subarray `[1,1,1]`)

---

## 🔹Approach 2: Prefix Sum + HashMap (O(n))

Use prefix sum and store first occurrence in a HashMap.

```java
// Optimal: O(n)
import java.util.*;

public class LongestSubarraySumK {
    public static int longestSubarray(int[] arr, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        int sum = 0, maxLen = 0;

        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];

            // Case 1: whole subarray [0..i] has sum k
            if (sum == k) {
                maxLen = i + 1;
            }

            // Case 2: Check if (sum - k) existed before
            if (map.containsKey(sum - k)) {
                maxLen = Math.max(maxLen, i - map.get(sum - k));
            }

            // Store first occurrence of prefix sum
            if (!map.containsKey(sum)) {
                map.put(sum, i);
            }
        }

        return maxLen;
    }

    public static void main(String[] args) {
        int[] arr = {10, 5, 2, 7, 1, 9};
        int k = 15;
        System.out.println("Longest Subarray Length = " + longestSubarray(arr, k));
    }
}
```

✅ Input: `arr = [10,5,2,7,1,9], k = 15`
✅ Output: `4` (subarray `[5,2,7,1]`)

---

## 🔹Approach 3: Sliding Window (O(n)) – Only for **Positive Integers**

Works only when all numbers are positive.

```java
// Sliding Window: O(n) (only for positive numbers)
public class LongestSubarraySumK {
    public static int longestSubarray(int[] arr, int k) {
        int left = 0, right = 0, sum = 0, maxLen = 0;

        while (right < arr.length) {
            sum += arr[right];

            // Shrink window if sum > k
            while (sum > k) {
                sum -= arr[left];
                left++;
            }

            if (sum == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }

            right++;
        }

        return maxLen;
    }

    public static void main(String[] args) {
        int[] arr = {1,2,1,1,1,3,2,1};
        int k = 5;
        System.out.println("Longest Subarray Length = " + longestSubarray(arr, k));
    }
}
```

✅ Input: `arr = [1,2,1,1,1,3,2,1], k = 5`
✅ Output: `4` (subarray `[1,1,1,2]`)

---

## ⏱ Time Complexities

1. Brute Force → **O(n²)**
2. Prefix Sum + HashMap → **O(n)** (works for positives + negatives)
3. Sliding Window → **O(n)** (works only for positives)

---

👉 Swathi, do you want me to **dry run the HashMap approach** step by step (since it’s the most asked in interviews), so you’ll get clarity on how the prefix sums are tracked?

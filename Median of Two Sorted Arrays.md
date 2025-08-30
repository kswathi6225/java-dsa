Great one 👍 "Median of Two Sorted Arrays" is a **very common interview problem (LeetCode #4)**.
I’ll give you **all main approaches** with **Java code, input/output, time & space complexity**.

---

## 🔹 Problem

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the **median of the two sorted arrays**.
The overall run time complexity should be `O(log(min(m,n)))` (for optimal solution).

---

## 1️⃣ Brute Force (Merge and Find Median)

👉 Merge both arrays, then find median like normal.

### Code

```java
import java.util.*;

public class MedianSortedArrays {
    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m = nums1.length, n = nums2.length;
        int[] merged = new int[m + n];
        
        int i = 0, j = 0, k = 0;
        while(i < m && j < n){
            if(nums1[i] < nums2[j]){
                merged[k++] = nums1[i++];
            } else {
                merged[k++] = nums2[j++];
            }
        }
        while(i < m) merged[k++] = nums1[i++];
        while(j < n) merged[k++] = nums2[j++];
        
        int total = m + n;
        if(total % 2 == 1) return merged[total/2];
        else return (merged[total/2 - 1] + merged[total/2]) / 2.0;
    }

    public static void main(String[] args) {
        int[] nums1 = {1, 3};
        int[] nums2 = {2};
        System.out.println(findMedianSortedArrays(nums1, nums2)); // 2.0

        int[] nums3 = {1, 2};
        int[] nums4 = {3, 4};
        System.out.println(findMedianSortedArrays(nums3, nums4)); // 2.5
    }
}
```

### Complexity

* **Time:** `O(m+n)` (merging)
* **Space:** `O(m+n)` (extra merged array)

---

## 2️⃣ Without Full Merge (Two Pointers)

👉 Instead of merging whole arrays, stop once you reach the middle index.

### Code

```java
public class MedianSortedArrays2 {
    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m = nums1.length, n = nums2.length;
        int total = m + n;
        int mid1 = (total - 1) / 2, mid2 = total / 2;

        int i = 0, j = 0, count = 0, val1 = 0, val2 = 0;

        while (count <= mid2) {
            int val;
            if (i < m && (j >= n || nums1[i] <= nums2[j])) {
                val = nums1[i++];
            } else {
                val = nums2[j++];
            }

            if (count == mid1) val1 = val;
            if (count == mid2) val2 = val;
            count++;
        }

        return (val1 + val2) / 2.0;
    }

    public static void main(String[] args) {
        int[] nums1 = {1, 3};
        int[] nums2 = {2};
        System.out.println(findMedianSortedArrays(nums1, nums2)); // 2.0
    }
}
```

### Complexity

* **Time:** `O(m+n)` (but stops earlier than merging fully)
* **Space:** `O(1)`

---

## 3️⃣ Optimal Binary Search (Partition Method)

👉 Use binary search on the smaller array.
Partition both arrays such that **left half ≤ right half**, then median comes from boundary values.

### Code

```java
public class MedianSortedArraysOptimal {
    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) 
            return findMedianSortedArrays(nums2, nums1); // ensure nums1 is smaller

        int m = nums1.length, n = nums2.length;
        int low = 0, high = m;

        while (low <= high) {
            int cut1 = (low + high) / 2;
            int cut2 = (m + n + 1) / 2 - cut1;

            int left1 = (cut1 == 0) ? Integer.MIN_VALUE : nums1[cut1 - 1];
            int left2 = (cut2 == 0) ? Integer.MIN_VALUE : nums2[cut2 - 1];
            int right1 = (cut1 == m) ? Integer.MAX_VALUE : nums1[cut1];
            int right2 = (cut2 == n) ? Integer.MAX_VALUE : nums2[cut2];

            if (left1 <= right2 && left2 <= right1) {
                if ((m + n) % 2 == 0) {
                    return (Math.max(left1, left2) + Math.min(right1, right2)) / 2.0;
                } else {
                    return Math.max(left1, left2);
                }
            } else if (left1 > right2) {
                high = cut1 - 1;
            } else {
                low = cut1 + 1;
            }
        }
        return 0.0; // never happens
    }

    public static void main(String[] args) {
        int[] nums1 = {1, 3};
        int[] nums2 = {2};
        System.out.println(findMedianSortedArrays(nums1, nums2)); // 2.0

        int[] nums3 = {1, 2};
        int[] nums4 = {3, 4};
        System.out.println(findMedianSortedArrays(nums3, nums4)); // 2.5
    }
}
```

### Complexity

* **Time:** `O(log(min(m, n)))`
* **Space:** `O(1)` (best possible)

---

## 📊 Summary Table

| Approach                | Time Complexity    | Space    | Notes                                |
| ----------------------- | ------------------ | -------- | ------------------------------------ |
| Merge & Median          | `O(m+n)`           | `O(m+n)` | Simple but heavy                     |
| Two-Pointer (No Merge)  | `O(m+n)`           | `O(1)`   | Lighter, avoids storing merged array |
| Binary Search Partition | `O(log(min(m,n)))` | `O(1)`   | Best, required in interviews         |

---

👉 Swathi, do you want me to also make a **dry run table** for the **binary search optimal approach** (with example like `[1,3]` and `[2]`), so you can clearly see how the partitions move?

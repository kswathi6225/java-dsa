Great question 👍 Peak Element is a **classic interview problem**!

---

## 🔹 Problem: Find Peak Element

A **peak element** in an array is one that is **not smaller than its neighbors**.
Formally, for index `i`:

* `arr[i] >= arr[i-1]` (if `i > 0`)
* `arr[i] >= arr[i+1]` (if `i < n-1`)

You need to return **any one peak element index**.

---

## ✅ Brute Force Approach

* Traverse the array and check for each element if it is a peak.
* Time: **O(n)**
* Space: **O(1)**

```java
public class PeakElement {
    public static int findPeakBrute(int[] arr) {
        int n = arr.length;

        if (n == 1) return 0; // only one element
        if (arr[0] >= arr[1]) return 0; // first element peak
        if (arr[n-1] >= arr[n-2]) return n-1; // last element peak

        for (int i = 1; i < n-1; i++) {
            if (arr[i] >= arr[i-1] && arr[i] >= arr[i+1]) {
                return i;
            }
        }
        return -1; // won't happen if input is valid
    }

    public static void main(String[] args) {
        int arr[] = {1, 3, 20, 4, 1, 0};
        System.out.println("Peak found at index: " + findPeakBrute(arr));
    }
}
```

---

## 🚀 Optimized Approach (Binary Search)

Since at least **one peak always exists**, we can apply binary search.

### Logic:

* Find mid = `(low+high)/2`
* If `arr[mid]` is peak → return `mid`
* Else if `arr[mid] < arr[mid+1]` → move **right**
* Else → move **left**

⏱ Time: **O(log n)**
📦 Space: **O(1)**

```java
public class PeakElementBinarySearch {
    public static int findPeakBinary(int[] arr) {
        int low = 0, high = arr.length - 1;

        while (low < high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] < arr[mid + 1]) {
                // move right
                low = mid + 1;
            } else {
                // move left (mid could be peak)
                high = mid;
            }
        }
        return low; // low == high
    }

    public static void main(String[] args) {
        int arr[] = {1, 3, 20, 4, 1, 0};
        int index = findPeakBinary(arr);
        System.out.println("Peak element is " + arr[index] + " at index " + index);
    }
}
```

---

✅ Example:
Input: `[1, 3, 20, 4, 1, 0]`
Output: `20` at index `2` (peak element).

---

Do you want me to also cover the **variation "Find Peak in a 2D Matrix"** (common interview follow-up)?

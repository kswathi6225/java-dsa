Great question 🚀 Let’s break it down clearly:

We need to **count the occurrences of a number in a sorted array that may contain duplicates**.
👉 Idea: Use **Binary Search** to find the **first occurrence** and the **last occurrence** of the number.
Then, the count = `(lastIndex - firstIndex + 1)`

---

## ✅ Approach 1: Binary Search (Efficient)

* **Time Complexity:** `O(log n)`
* **Space Complexity:** `O(1)`

```java
public class CountOccurrences {

    // Function to find first occurrence of target
    static int firstOccurrence(int[] arr, int target) {
        int low = 0, high = arr.length - 1, ans = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                ans = mid;
                high = mid - 1; // keep searching left
            } else if (arr[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return ans;
    }

    // Function to find last occurrence of target
    static int lastOccurrence(int[] arr, int target) {
        int low = 0, high = arr.length - 1, ans = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                ans = mid;
                low = mid + 1; // keep searching right
            } else if (arr[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return ans;
    }

    // Count occurrences using above helpers
    static int countOccurrences(int[] arr, int target) {
        int first = firstOccurrence(arr, target);
        if (first == -1) return 0; // not found
        int last = lastOccurrence(arr, target);
        return last - first + 1;
    }

    // Driver code
    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 2, 3, 4, 5};
        int target = 2;

        int count = countOccurrences(arr, target);
        System.out.println("Count of " + target + " = " + count);
    }
}
```

**Output:**

```
Count of 2 = 3
```

---

## ✅ Approach 2: Linear Scan (Naive)

* Just iterate and count.
* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

```java
int count = 0;
for (int num : arr) {
    if (num == target) count++;
}
```

---

👉 For interviews, **Approach 1 (Binary Search)** is the expected solution.

Would you like me to also give you the **recursive binary search version** (some interviewers like to ask)?

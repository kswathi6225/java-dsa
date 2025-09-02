Great one 🚀 — **Floor and Ceil in a Sorted Array** is a very common interview question. Let’s break it down.

---

## 🔹 Problem Definition

* **Floor of x** = Largest element ≤ x in the array.
* **Ceil of x** = Smallest element ≥ x in the array.
* Array is **sorted** in ascending order.

---

## 🔹 Approaches

### **1. Linear Search (Naive)**

* Traverse the array and keep track of floor and ceil.
* **Time:** `O(n)`
* **Space:** `O(1)`

---

### **2. Binary Search (Optimized) ✅**

* Since the array is sorted, use binary search.
* Keep adjusting left/right pointers and track candidates for floor/ceil.

**Time:** `O(log n)`
**Space:** `O(1)`

---

## 🔹 Code (Java) – Binary Search Approach

```java
import java.util.*;

public class FloorCeilInSortedArray {

    // Function to find floor
    public static int findFloor(int[] arr, int x) {
        int low = 0, high = arr.length - 1;
        int floor = -1; // If no floor exists

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == x) {
                return arr[mid]; // Exact match is both floor and ceil
            }
            if (arr[mid] < x) {
                floor = arr[mid]; // Candidate for floor
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return floor;
    }

    // Function to find ceil
    public static int findCeil(int[] arr, int x) {
        int low = 0, high = arr.length - 1;
        int ceil = -1; // If no ceil exists

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == x) {
                return arr[mid]; // Exact match
            }
            if (arr[mid] > x) {
                ceil = arr[mid]; // Candidate for ceil
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ceil;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10, 12};
        int x = 7;

        int floor = findFloor(arr, x);
        int ceil = findCeil(arr, x);

        System.out.println("Element: " + x);
        System.out.println("Floor: " + floor);
        System.out.println("Ceil: " + ceil);
    }
}
```

---

## 🔹 Example Run

Input: `arr = [2, 4, 6, 8, 10, 12], x = 7`
Output:

```
Element: 7
Floor: 6
Ceil: 8
```

---

⚡ This **binary search approach** is the most efficient (`O(log n)`), widely expected in interviews.

Would you like me to also show you how to handle **multiple queries of floor/ceil efficiently** (like for `q` different values)? That’s another common twist.

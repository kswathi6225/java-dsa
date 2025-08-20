
# 📌 Merge Sort in Java

### ✅ Code:

```java
public class MergeSort {
    // Function to merge two sorted subarrays
    public static void conquer(int[] arr, int st, int mid, int ed) {
        int merged[] = new int[ed - st + 1];
        int index1 = st;
        int index2 = mid + 1;
        int x = 0;

        // Merge the two halves
        while (index1 <= mid && index2 <= ed) {
            if (arr[index1] <= arr[index2]) {
                merged[x++] = arr[index1++];
            } else {
                merged[x++] = arr[index2++];
            }
        }

        // Copy remaining elements of left part
        while (index1 <= mid) {
            merged[x++] = arr[index1++];
        }

        // Copy remaining elements of right part
        while (index2 <= ed) {
            merged[x++] = arr[index2++];
        }

        // Copy merged array back into original array
        for (int i = 0, j = st; i < merged.length; i++, j++) {
            arr[j] = merged[i];
        }
    }

    // Function to divide the array
    public static void divide(int[] arr, int st, int ed) {
        if (st >= ed) {
            return; // base case
        }

        int mid = st + (ed - st) / 2;
        divide(arr, st, mid);       // left half
        divide(arr, mid + 1, ed);   // right half
        conquer(arr, st, mid, ed);  // merge step
    }

    // Driver code
    public static void main(String[] args) {
        int arr[] = {6, 7, 4, 3, 9, 2};
        int n = arr.length;

        System.out.println("Original Array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        divide(arr, 0, n - 1);

        System.out.println("Sorted Array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

### ✅ Input:

```
6 7 4 3 9 2
```

### ✅ Output:

```
Original Array:
6 7 4 3 9 2 

Sorted Array:
2 3 4 6 7 9
```

---

### ✅ Time Complexity:

* **Best Case:** O(n log n)
* **Average Case:** O(n log n)
* **Worst Case:** O(n log n)

### ✅ Space Complexity:

* **O(n)** (due to temporary merged arrays)

---

👉 This is the complete working **Merge Sort** implementation with explanation.

Do you also want me to give you a **step-by-step dry run** for your input `[6,7,4,3,9,2]` so you can visualize how merge sort works internally?

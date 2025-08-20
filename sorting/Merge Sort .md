

## **Merge Sort on Array (Java)**

```java
public class MergeSortArray {

    // MergeSort function
    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = left + (right - left) / 2;

            // Sort first and second halves
            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);

            // Merge sorted halves
            merge(arr, left, mid, right);
        }
    }

    // Merge two sorted halves
    private static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] L = new int[n1];
        int[] R = new int[n2];

        // Copy data to temp arrays
        for (int i = 0; i < n1; i++) L[i] = arr[left + i];
        for (int j = 0; j < n2; j++) R[j] = arr[mid + 1 + j];

        int i = 0, j = 0, k = left;

        // Merge back into original array
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements
        while (i < n1) arr[k++] = L[i++];
        while (j < n2) arr[k++] = R[j++];
    }

    // Print array
    public static void printArray(int[] arr) {
        for (int num : arr) System.out.print(num + " ");
        System.out.println();
    }

    // Main method
    public static void main(String[] args) {
        int[] arr = {4, 2, 1, 3};
        System.out.print("Original Array: ");
        printArray(arr);

        mergeSort(arr, 0, arr.length - 1);

        System.out.print("Sorted Array: ");
        printArray(arr);
    }
}
```

---

### **Output**

```
Original Array: 4 2 1 3 
Sorted Array: 1 2 3 4 
```

---

### **Time and Space Complexity**

| Case               | Time Complexity | Space Complexity         |
| ------------------ | --------------- | ------------------------ |
| Best/Average/Worst | O(n log n)      | O(n) (extra temp arrays) |

* Merge Sort **always divides the array in half** → guarantees O(n log n).
* Requires extra space for temporary arrays → not in-place.

---

I can also provide a **linked-list merge sort version** optimized for O(1) space if you want.

Do you want me to do that?

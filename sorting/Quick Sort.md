## **Quick Sort on Array (Java)**

```java
public class QuickSortArray {

    // QuickSort function
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);

            // Recursively sort elements before and after partition
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    // Partition function
    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[high]; // choose last element as pivot
        int i = low - 1; // index of smaller element

        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                // swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // swap arr[i+1] and arr[high] (pivot)
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        return i + 1;
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

        quickSort(arr, 0, arr.length - 1);

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

| Case                 | Time Complexity | Space Complexity         |
| -------------------- | --------------- | ------------------------ |
| Best/Average         | O(n log n)      | O(log n) recursion stack |
| Worst (sorted array) | O(n²)           | O(log n)                 |

* Pivot choice affects performance: choosing **last element** is simple but can lead to worst-case on sorted/reverse arrays.
* Randomized pivot can reduce worst-case probability.

---

If you want, I can also give the **Quick Sort code using randomized pivot** for arrays, which is more optimal for interviews.

Do you want me to do that?

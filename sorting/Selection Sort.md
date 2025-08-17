# Selection Sort in Java

## Concept
Selection Sort is a simple comparison-based sorting algorithm.  
It repeatedly selects the **smallest element** from the unsorted portion of the array and places it in its correct position.

---

## Example

### Input:
```

64, 25, 12, 22, 11

```

### Output:
```

11, 12, 22, 25, 64

````

---

## Dry Run (Step by Step Execution)

Initial Array: **[64, 25, 12, 22, 11]**

| Pass | Unsorted Portion            | Minimum Found | Swap                | Resulting Array         |
|------|-----------------------------|---------------|---------------------|-------------------------|
| 1    | [64, 25, 12, 22, 11]        | 11            | Swap(64, 11)        | [11, 25, 12, 22, 64]    |
| 2    | [25, 12, 22, 64]            | 12            | Swap(25, 12)        | [11, 12, 25, 22, 64]    |
| 3    | [25, 22, 64]                | 22            | Swap(25, 22)        | [11, 12, 22, 25, 64]    |
| 4    | [25, 64]                    | 25            | No Swap Needed      | [11, 12, 22, 25, 64]    |
| 5    | [64]                        | Already Sorted| -                   | [11, 12, 22, 25, 64]    |

Final Sorted Array: **[11, 12, 22, 25, 64]**

---

## Time & Space Complexity

- **Best Case:** O(n²)  
- **Worst Case:** O(n²)  
- **Average Case:** O(n²)  
- **Space Complexity:** O(1) (In-place sorting)

---

## Java Code

```java
// Java program for implementation of Selection Sort
import java.util.Arrays;

class GfG {

    static void selectionSort(int[] arr){
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
          
            // Assume the current position holds the minimum element
            int min_idx = i;

            // Find the actual minimum in the unsorted portion
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[min_idx]) {
                    min_idx = j;
                }
            }

            // Swap the found minimum element with the first element
            int temp = arr[i];
            arr[i] = arr[min_idx];
            arr[min_idx] = temp;           
        }
    }

    static void printArray(int[] arr){
        for (int val : arr) {
            System.out.print(val + " ");
        }
        System.out.println();
    }
  
    public static void main(String[] args){
        int[] arr = { 64, 25, 12, 22, 11 };

        System.out.print("Original array: ");
        printArray(arr);

        selectionSort(arr);

        System.out.print("Sorted array: ");
        printArray(arr);
    }
}
````



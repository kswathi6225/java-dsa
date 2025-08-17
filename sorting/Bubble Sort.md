# 🫧 Bubble Sort

## 📌 Idea

Bubble Sort is a **comparison-based sorting algorithm**.
It repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.
This process continues until the list is sorted.

---

## 📥 Input Example

```
arr = [5, 3, 8, 4, 2]
```

---

## 🔄 Working (Step by Step)

1. Compare **5 and 3** → swap → `[3, 5, 8, 4, 2]`
2. Compare **5 and 8** → no swap → `[3, 5, 8, 4, 2]`
3. Compare **8 and 4** → swap → `[3, 5, 4, 8, 2]`
4. Compare **8 and 2** → swap → `[3, 5, 4, 2, 8]` ✅ (largest element moved to end)

Repeat the process for the remaining array until sorted.

Final sorted array →

```
[2, 3, 4, 5, 8]
```

---

## 📤 Output

```
Sorted array: [2, 3, 4, 5, 8]
```

---

## ⏳ Time Complexity

* **Best Case (already sorted):** `O(n)`
* **Average Case:** `O(n^2)`
* **Worst Case (reverse sorted):** `O(n^2)`

## 💾 Space Complexity

* **O(1)** → In-place sorting (no extra memory needed).

---

## 💻 Java Code

```java
import java.util.Arrays;

public class Main {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        
        // Outer loop for passes
        for (int i = 0; i < n - 1; i++) {
            boolean swapped = false;
            
            // Inner loop for comparing adjacent elements
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap elements
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            
            // If no swaps, array is already sorted
            if (!swapped) break;
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 4, 2};
        System.out.println("Original array: " + Arrays.toString(arr));
        
        bubbleSort(arr);
        
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }
}
```


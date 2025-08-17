# Insertion Sort in Java

## 📌 Explanation
Insertion Sort is a simple sorting algorithm that works similar to how we sort playing cards in our hands.  
We pick one element at a time and insert it into its correct position relative to the already sorted part of the array.  

---

## 📥 Input
```

arr = \[12, 11, 13, 5, 6]

```

## 📤 Output
```

Sorted array = \[5, 6, 11, 12, 13]

````

---

## 🧮 Dry Run (Step by Step)

| Iteration | Key | Compared With | Array State               |
|-----------|-----|---------------|---------------------------|
| i = 1     | 11  | 12            | [11, 12, 13, 5, 6]        |
| i = 2     | 13  | 12 (No shift) | [11, 12, 13, 5, 6]        |
| i = 3     | 5   | 13, 12, 11    | [5, 11, 12, 13, 6]        |
| i = 4     | 6   | 13, 12, 11    | [5, 6, 11, 12, 13]        |

✅ Final Sorted Array: **[5, 6, 11, 12, 13]**

---

## ⚡ Time Complexity
- **Best Case (Already Sorted):** O(n)  
- **Worst Case (Reverse Sorted):** O(n²)  
- **Average Case:** O(n²)  
- **Space Complexity:** O(1) (In-place sorting)  

---

## 💻 Java Code

```java
// Java program for implementation of Insertion Sort
public class InsertionSort {
    /* Function to sort array using insertion sort */
    void sort(int arr[]) {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;

            // Move elements of arr[0..i-1], that are greater than key
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }

    /* A utility function to print array of size n */
    static void printArray(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }

    // Driver method
    public static void main(String args[]) {
        int arr[] = { 12, 11, 13, 5, 6 };

        InsertionSort ob = new InsertionSort();
        ob.sort(arr);

        printArray(arr);
    }
}
````

```

Would you also like me to make a **side-by-side dry run (iteration + array update)** visualization like a trace diagram (good for interviews)?
```

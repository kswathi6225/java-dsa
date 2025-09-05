Got it 👍
I’ll write the **Java solution** step by step for your **Coding Question 11**.

---

## ✅ Problem Restatement

1. Input size `n`.
2. Input `n` elements of the array.
3. Split into **even-indexed array** and **odd-indexed array**.

   * index `0, 2, 4, ...` → even array
   * index `1, 3, 5, ...` → odd array
4. Sort both arrays in ascending order.
5. Find **second largest** in both arrays.
6. Print their sum.

---

## ✅ Code

```java
import java.util.*;

public class CodingQuestion11 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Step 1: Input size
        System.out.print("Enter the size of array: ");
        int n = sc.nextInt();

        int[] arr = new int[n];

        // Step 2: Input elements
        for (int i = 0; i < n; i++) {
            System.out.print("Enter element at " + i + " index: ");
            arr[i] = sc.nextInt();
        }

        // Step 3: Separate even-indexed and odd-indexed
        List<Integer> even = new ArrayList<>();
        List<Integer> odd = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                even.add(arr[i]);
            } else {
                odd.add(arr[i]);
            }
        }

        // Step 4: Sort both
        Collections.sort(even);
        Collections.sort(odd);

        System.out.print("Sorted even array: ");
        for (int x : even) System.out.print(x + " ");
        System.out.println();

        System.out.print("Sorted odd array: ");
        for (int x : odd) System.out.print(x + " ");
        System.out.println();

        // Step 5: Find second largest
        int evenSecondLargest = -1;
        int oddSecondLargest = -1;

        if (even.size() >= 2) {
            evenSecondLargest = even.get(even.size() - 2);
        } else if (even.size() == 1) {
            evenSecondLargest = even.get(0); // only one element
        }

        if (odd.size() >= 2) {
            oddSecondLargest = odd.get(odd.size() - 2);
        } else if (odd.size() == 1) {
            oddSecondLargest = odd.get(0); // only one element
        }

        // Step 6: Print sum
        int sum = evenSecondLargest + oddSecondLargest;
        System.out.println("Sum of second largest elements: " + sum);
    }
}
```

---

## ✅ Example Run

Input:

```
Enter the size of array: 5
Enter element at 0 index: 3
Enter element at 1 index: 4
Enter element at 2 index: 1
Enter element at 3 index: 7
Enter element at 4 index: 9
```

Output:

```
Sorted even array: 1 3 9
Sorted odd array: 4 7
Sum of second largest elements: 3 + 4 = 7
```

---

👉 This handles cases where arrays have only **1 element** too.

Do you want me to also write the **optimized version (without sorting, directly finding second largest)**?

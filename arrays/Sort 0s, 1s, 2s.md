Perfect 🚀 You want the **three approaches for sorting an array of 0s, 1s, and 2s (Sort Colors problem)** but in **Java**.
I’ll keep the structure exactly like your C++ explanation with Java code for each approach.

---

# 🔵 Sort 0s, 1s, 2s (a.k.a Sort Colors)

Input Example:

```java
int[] arr = {2, 0, 1, 2, 1, 0, 1, 2};
```

---

## ✅ Approach 1: Brute Force using `Arrays.sort()`

> 🔹 Time Complexity: `O(n log n)`
> 🔹 Space Complexity: `O(1)`

```java
import java.util.*;

public class Main {
    public static void sortBrute(int[] arr) {
        Arrays.sort(arr); // Inbuilt sort
    }

    public static void main(String[] args) {
        int[] arr = {2, 0, 1, 2, 1, 0, 1, 2};
        sortBrute(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```

---

## ✅ Approach 2: Counting Sort (Count 0s, 1s, 2s)

> 🔹 Time Complexity: `O(n)`
> 🔹 Space Complexity: `O(1)`

```java
import java.util.*;

public class Main {
    public static void sort012(int[] arr) {
        int count0 = 0, count1 = 0, count2 = 0;

        // Count frequencies
        for (int num : arr) {
            if (num == 0) count0++;
            else if (num == 1) count1++;
            else count2++;
        }

        int idx = 0;
        for (int i = 0; i < count0; i++) arr[idx++] = 0;
        for (int i = 0; i < count1; i++) arr[idx++] = 1;
        for (int i = 0; i < count2; i++) arr[idx++] = 2;
    }

    public static void main(String[] args) {
        int[] arr = {2, 0, 2, 1, 1, 0, 1, 2, 0, 0};
        sort012(arr);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }
}
```

---

## ✅ Approach 3: Dutch National Flag Algorithm (Most Optimal)

> 🔹 Time Complexity: `O(n)`
> 🔹 Space Complexity: `O(1)`
> 🔹 Uses **3 pointers**: `low`, `mid`, `high`

```java
import java.util.*;

public class Main {
    public static void sortDNF(int[] arr) {
        int low = 0, mid = 0;
        int high = arr.length - 1;

        while (mid <= high) {
            if (arr[mid] == 0) {
                int temp = arr[low];
                arr[low] = arr[mid];
                arr[mid] = temp;
                low++;
                mid++;
            } 
            else if (arr[mid] == 1) {
                mid++;
            } 
            else { // arr[mid] == 2
                int temp = arr[mid];
                arr[mid] = arr[high];
                arr[high] = temp;
                high--;
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {2, 0, 1, 2, 1, 0, 1, 2};
        sortDNF(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```

---

## 🔍 Summary Table

| Approach               | Time       | Space | Stable | Comment                     |
| ---------------------- | ---------- | ----- | ------ | --------------------------- |
| Inbuilt sort (Brute)   | O(n log n) | O(1)  | Yes    | Easiest, but not optimal    |
| Counting Sort (Better) | O(n)       | O(1)  | No     | Good if data is only 0,1,2  |
| DNF (Optimal)          | O(n)       | O(1)  | No     | Best approach (Single Pass) |

---

✨ The **Dutch National Flag (DNF)** approach is the one usually expected in interviews.

Do you want me to also **dry run the DNF approach step by step** with your input `{2,0,1,2,1,0,1,2}` so you can visualize how the pointers move?

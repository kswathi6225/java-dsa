# 📌 Sort an Array of 0s, 1s, and 2s (Java)

---

## ✅ **Approach 1: Brute Force using `Arrays.sort()`**

> 🔹 Time Complexity: `O(n log n)`
> 🔹 Space Complexity: `O(1)`

```java
import java.util.Arrays;

public class SortColorsBrute {
    public static void sortBrute(int[] arr) {
        Arrays.sort(arr); // Inbuilt sort
    }

    public static void main(String[] args) {
        int[] arr = {2, 0, 1, 2, 1, 0, 1, 2};
        sortBrute(arr);
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

## ✅ **Approach 2: Counting Sort**

> 🔹 Time Complexity: `O(n)`
> 🔹 Space Complexity: `O(1)`

```java
public class SortColorsCount {
    public static void sort012(int[] arr) {
        int count0 = 0, count1 = 0, count2 = 0;

        for (int num : arr) {
            if (num == 0) count0++;
            else if (num == 1) count1++;
            else count2++;
        }

        int index = 0;
        for (int i = 0; i < count0; i++) arr[index++] = 0;
        for (int i = 0; i < count1; i++) arr[index++] = 1;
        for (int i = 0; i < count2; i++) arr[index++] = 2;
    }

    public static void main(String[] args) {
        int[] arr = {2, 0, 2, 1, 1, 0, 1, 2, 0, 0};
        sort012(arr);

        System.out.print("Sorted Array: ");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

## ✅ **Approach 3: Dutch National Flag (Optimal)**

> 🔹 Time Complexity: `O(n)`
> 🔹 Space Complexity: `O(1)`

```java
public class SortColorsDNF {
    public static void sortDNF(int[] arr) {
        int low = 0, mid = 0, high = arr.length - 1;

        while (mid <= high) {
            if (arr[mid] == 0) {
                // swap arr[low] and arr[mid]
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

        System.out.print("Sorted Array: ");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

## 🔍 Summary Table (Java)

| Approach                | Time       | Space | Stable | Comment                     |
| ----------------------- | ---------- | ----- | ------ | --------------------------- |
| `Arrays.sort()` (Brute) | O(n log n) | O(1)  | Yes    | Simple but not optimal      |
| Counting Sort (Better)  | O(n)       | O(1)  | No     | Works only for 0,1,2 values |
| DNF (Optimal)           | O(n)       | O(1)  | No     | Best approach (Single Pass) |

---

👉 Do you want me to also make a **single Java file containing all three approaches** so you can run them one after another for practice?

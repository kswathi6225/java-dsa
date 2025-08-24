Great question 👍 Removing duplicates from an array in **Java** can be done in multiple ways. Let’s go step by step with **brute force** and **HashSet** approaches.

---

## ✅ 1. Brute Force (Using nested loops or extra array)

```java
import java.util.*;

public class RemoveDuplicatesBrute {
    public static void main(String[] args) {
        int[] arr = {4, 2, 4, 5, 2, 3, 1};

        // Sort first (optional but helps to remove duplicates easily)
        Arrays.sort(arr);

        int n = arr.length;
        int j = 0;

        // Keep only unique elements
        for (int i = 0; i < n - 1; i++) {
            if (arr[i] != arr[i + 1]) {
                arr[j++] = arr[i];
            }
        }
        arr[j++] = arr[n - 1]; // last element always unique

        System.out.print("Array without duplicates: ");
        for (int i = 0; i < j; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

👉 **Time Complexity:**

* Sorting = `O(n log n)`
* Removing duplicates = `O(n)`
* **Total = O(n log n)**

👉 **Space Complexity:** `O(1)` (in-place).

---

## ✅ 2. Using **HashSet** (Best & Simple)

```java
import java.util.*;

public class RemoveDuplicatesHashSet {
    public static void main(String[] args) {
        int[] arr = {4, 2, 4, 5, 2, 3, 1};

        HashSet<Integer> set = new HashSet<>();

        for (int num : arr) {
            set.add(num); // HashSet automatically removes duplicates
        }

        System.out.print("Array without duplicates: ");
        for (int num : set) {
            System.out.print(num + " ");
        }
    }
}
```

👉 **Time Complexity:**

* Inserting into HashSet = `O(n)` (on average).

👉 **Space Complexity:** `O(n)` (extra space for HashSet).

---

⚡ **Interview Tip:**

* If order doesn’t matter → use **HashSet**.
* If order must be preserved → use **LinkedHashSet**.
* If array must remain sorted → first sort, then remove duplicates in place.

---

Do you want me to also show the **LinkedHashSet** approach (to preserve original order)?

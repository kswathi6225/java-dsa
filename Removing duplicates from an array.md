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
Got it 👍 You can remove duplicates from an array in **Java** using a `LinkedHashSet`.
Why `LinkedHashSet`?

* **HashSet** removes duplicates but does not preserve order.
* **LinkedHashSet** removes duplicates **and preserves insertion order**.

Here’s the code ⬇️

```java
import java.util.*;

public class RemoveDuplicates {
    public static void main(String[] args) {
        int[] arr = {4, 5, 9, 4, 9, 7, 5, 2};

        // Step 1: Use LinkedHashSet to remove duplicates
        LinkedHashSet<Integer> set = new LinkedHashSet<>();
        for (int num : arr) {
            set.add(num); // duplicates will be ignored automatically
        }

        // Step 2: Convert back to array (optional)
        int[] uniqueArr = new int[set.size()];
        int i = 0;
        for (int num : set) {
            uniqueArr[i++] = num;
        }

        // Step 3: Print result
        System.out.println("Array after removing duplicates: " + Arrays.toString(uniqueArr));
    }
}
```

### ✅ Output:

```
Array after removing duplicates: [4, 5, 9, 7, 2]
```

---

### ⏱ Time Complexity:

* Inserting into `LinkedHashSet`: **O(n)** on average (since hashing is O(1) per insert).
* Copying back to array: **O(n)**.
  👉 Overall: **O(n)**

### 🗂 Space Complexity:

* Uses `LinkedHashSet` to store unique elements → **O(n)** in worst case (if all elements are unique).

---

Do you also want me to show the **brute force method (nested loops)** for removing duplicates in an array (without extra space)?

* If array must remain sorted → first sort, then remove duplicates in place.

---

Do you want me to also show the **LinkedHashSet** approach (to preserve original order)?

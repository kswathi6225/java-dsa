Perfect 💡 This is the **"Find Duplicate in an Array"** problem. Let’s solve it in **two ways**:

---

## ✅ Problem Statement:

Given an array of integers, find if there are any duplicates.

---

## 1. **Brute Force Approach**

We compare each element with every other element using two loops.

### Code (Java):

```java
public class Main {
    public static boolean hasDuplicateBruteForce(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (arr[i] == arr[j]) {
                    return true; // Duplicate found
                }
            }
        }
        return false; // No duplicates
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 4, 2, 5, 3};
        System.out.println("Duplicate present? " + hasDuplicateBruteForce(arr));
    }
}
```

### ⏱ Time Complexity:

* Outer loop: **O(n)**
* Inner loop: **O(n)**
  ➡ Overall: **O(n²)**

### 📦 Space Complexity:

* **O(1)** (no extra space)

---

## 2. **Optimized Approach using HashSet**

We use a **HashSet** to keep track of seen numbers.

### Code (Java):

```java
import java.util.*;

public class Main {
    public static boolean hasDuplicateHashSet(int[] arr) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : arr) {
            if (set.contains(num)) {
                return true; // Duplicate found
            }
            set.add(num);
        }
        return false; // No duplicates
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 4, 2, 5, 3};
        System.out.println("Duplicate present? " + hasDuplicateHashSet(arr));
    }
}
```

### ⏱ Time Complexity:

* Loop runs **O(n)** times
* `set.contains()` and `set.add()` are **O(1)** average case
  ➡ Overall: **O(n)**

### 📦 Space Complexity:

* **O(n)** (extra space for HashSet)

---

👉 So in interviews, you can say:

* **Brute Force (O(n²))** works but slow.
* **HashSet (O(n))** is efficient with extra space trade-off.

---

Do you want me to now take this **duplicate problem further** (like finding all duplicates, or the first duplicate index) so you become stronger at variations?

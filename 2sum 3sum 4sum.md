
---

# 🔹 **2Sum Problem**

**Problem**: Given an array `arr[]` and a target sum `k`, find if there exist two numbers whose sum is equal to `k`.

---

### **Approach 1: Brute Force (Check all pairs)**

* For each element, check every other element.

```java
import java.util.*;

public class TwoSumBrute {
    public static void main(String[] args) {
        int[] arr = {2, 7, 11, 15};
        int target = 9;

        for (int i = 0; i < arr.length; i++) {
            for (int j = i+1; j < arr.length; j++) {
                if (arr[i] + arr[j] == target) {
                    System.out.println("Pair: " + arr[i] + ", " + arr[j]);
                }
            }
        }
    }
}
```

✅ **Time Complexity:** `O(n^2)`
✅ **Space Complexity:** `O(1)`

---

### **Approach 2: Sorting + Two Pointers**

1. Sort array
2. Use left & right pointers

```java
import java.util.*;

public class TwoSumTwoPointer {
    public static void main(String[] args) {
        int[] arr = {2, 7, 11, 15};
        int target = 9;

        Arrays.sort(arr); // O(n log n)

        int left = 0, right = arr.length - 1;

        while (left < right) {
            int sum = arr[left] + arr[right];
            if (sum == target) {
                System.out.println("Pair: " + arr[left] + ", " + arr[right]);
                left++;
                right--;
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
    }
}
```

✅ **Time Complexity:** `O(n log n)` (sorting)
✅ **Space Complexity:** `O(1)`

---

### **Approach 3: Hashing (Most Optimal for 2Sum)**

* Use HashSet/HashMap to check if `target - arr[i]` exists.

```java
import java.util.*;

public class TwoSumHashing {
    public static void main(String[] args) {
        int[] arr = {2, 7, 11, 15};
        int target = 9;

        HashSet<Integer> set = new HashSet<>();

        for (int num : arr) {
            int complement = target - num;
            if (set.contains(complement)) {
                System.out.println("Pair: " + num + ", " + complement);
            }
            set.add(num);
        }
    }
}
```

✅ **Time Complexity:** `O(n)`
✅ **Space Complexity:** `O(n)`

---

# 🔹 **3Sum Problem**

**Problem**: Find all triplets in array whose sum = 0.

---

### **Approach 1: Brute Force (3 loops)**

```java
import java.util.*;

public class ThreeSumBrute {
    public static void main(String[] args) {
        int[] arr = {-1, 0, 1, 2, -1, -4};
        int n = arr.length;

        for (int i = 0; i < n; i++) {
            for (int j = i+1; j < n; j++) {
                for (int k = j+1; k < n; k++) {
                    if (arr[i] + arr[j] + arr[k] == 0) {
                        System.out.println(arr[i] + ", " + arr[j] + ", " + arr[k]);
                    }
                }
            }
        }
    }
}
```

✅ **Time Complexity:** `O(n^3)`
✅ **Space Complexity:** `O(1)`

---

### **Approach 2: Sorting + Two Pointers (Optimal)**

```java
import java.util.*;

public class ThreeSumTwoPointer {
    public static void main(String[] args) {
        int[] arr = {-1, 0, 1, 2, -1, -4};
        Arrays.sort(arr);

        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < arr.length - 2; i++) {
            if (i > 0 && arr[i] == arr[i-1]) continue; // avoid duplicates

            int left = i+1, right = arr.length - 1;

            while (left < right) {
                int sum = arr[i] + arr[left] + arr[right];

                if (sum == 0) {
                    result.add(Arrays.asList(arr[i], arr[left], arr[right]));
                    left++;
                    right--;
                    while (left < right && arr[left] == arr[left-1]) left++;
                    while (left < right && arr[right] == arr[right+1]) right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }

        System.out.println(result);
    }
}
```

✅ **Time Complexity:** `O(n^2)`
✅ **Space Complexity:** `O(1)` (excluding output)

---

# 🔹 **4Sum Problem**

**Problem**: Find all quadruplets whose sum = target.

---

### **Approach 1: Brute Force (4 loops)**

✅ Time: `O(n^4)` → Not practical.

---

### **Approach 2: Sorting + Two Pointers**

```java
import java.util.*;

public class FourSum {
    public static void main(String[] args) {
        int[] arr = {1, 0, -1, 0, -2, 2};
        int target = 0;
        Arrays.sort(arr);

        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < arr.length - 3; i++) {
            if (i > 0 && arr[i] == arr[i-1]) continue;

            for (int j = i+1; j < arr.length - 2; j++) {
                if (j > i+1 && arr[j] == arr[j-1]) continue;

                int left = j+1, right = arr.length - 1;

                while (left < right) {
                    int sum = arr[i] + arr[j] + arr[left] + arr[right];

                    if (sum == target) {
                        result.add(Arrays.asList(arr[i], arr[j], arr[left], arr[right]));
                        left++;
                        right--;
                        while (left < right && arr[left] == arr[left-1]) left++;
                        while (left < right && arr[right] == arr[right+1]) right--;
                    } else if (sum < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }

        System.out.println(result);
    }
}
```

✅ **Time Complexity:** `O(n^3)`
✅ **Space Complexity:** `O(1)` (excluding output)

---

# 🔹 Summary of Time Complexities

* **2Sum**:

  * Brute: `O(n^2)`
  * Sorting + Two Pointers: `O(n log n)`
  * Hashing: `O(n)` ✅ Optimal

* **3Sum**:

  * Brute: `O(n^3)`
  * Sorting + Two Pointers: `O(n^2)` ✅ Optimal

* **4Sum**:

  * Brute: `O(n^4)`
  * Sorting + Two Pointers: `O(n^3)` ✅ Optimal

---

👉 Swathi, do you want me to **give you 1 practice problem on 2Sum first** (you solve with Hashing), and then we continue with 3Sum & 4Sum practice step by step?


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

public class Main {
    public static List<List<Integer>> triplet(int n, int[] arr) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(arr);

        for (int i = 0; i < n; i++) {
            //remove duplicates:
            if (i != 0 && arr[i] == arr[i - 1]) continue;

            //moving 2 pointers:
            int j = i + 1;
            int k = n - 1;
            while (j < k) {
                int sum = arr[i] + arr[j] + arr[k];
                if (sum < 0) {
                    j++;
                } else if (sum > 0) {
                    k--;
                } else {
                    List<Integer> temp = Arrays.asList(arr[i], arr[j], arr[k]);
                    ans.add(temp);
                    j++;
                    k--;
                    //skip the duplicates:
                    while (j < k && arr[j] == arr[j - 1]) j++;
                    while (j < k && arr[k] == arr[k + 1]) k--;
                }
            }
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] arr = { -1, 0, 1, 2, -1, -4};
        int n = arr.length;
        List<List<Integer>> ans = triplet(n, arr);
        for (List<Integer> it : ans) {
                System.out.print(it);
        }
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

public class Main {
    public static List<List<Integer>> fourSum(int[] nums, int target) {
        int n = nums.length; // size of the array
        List<List<Integer>> ans = new ArrayList<>();

        // sort the given array:
        Arrays.sort(nums);

        // calculating the quadruplets:
        for (int i = 0; i < n; i++) {
            // avoid the duplicates while moving i:
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            for (int j = i + 1; j < n; j++) {
                // avoid the duplicates while moving j:
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;

                // 2 pointers:
                int k = j + 1;
                int l = n - 1;
                while (k < l) {
                    long sum = nums[i];
                    sum += nums[j];
                    sum += nums[k];
                    sum += nums[l];
                    if (sum == target) {
                        List<Integer> temp = new ArrayList<>();
                        temp.add(nums[i]);
                        temp.add(nums[j]);
                        temp.add(nums[k]);
                        temp.add(nums[l]);
                        ans.add(temp);
                        k++;
                        l--;

                        // skip the duplicates:
                        while (k < l && nums[k] == nums[k - 1]) k++;
                        while (k < l && nums[l] == nums[l + 1]) l--;
                    } else if (sum < target) k++;
                    else l--;
                }
            }
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] nums = {4, 3, 3, 4, 4, 2, 1, 2, 1, 1};
        int target = 9;
        List<List<Integer>> ans = fourSum(nums, target);
        System.out.println("The quadruplets are: ");
        for (List<Integer> it : ans) {
            System.out.print(it+" ");
        }
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

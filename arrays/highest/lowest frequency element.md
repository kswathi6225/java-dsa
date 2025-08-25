# ❓ Problem:

Given an array of integers, find the element with the **highest frequency** (most occurrences) and the one with the **lowest frequency** (least occurrences).

Example:

```
Input:  [2, 3, 2, 4, 5, 3, 2, 4]
Output: Highest = 2 (occurs 3 times), Lowest = 5 (occurs 1 time)
```

---

## ✅ Approach 1: Brute Force

* For each element, count its frequency using a nested loop.
* Track max and min.

### Code (Brute Force):

```java
import java.util.*;

public class Frequency {
    public static void main(String[] args) {
        int[] arr = {2, 3, 2, 4, 5, 3, 2, 4};

        int n = arr.length;
        int maxFreq = Integer.MIN_VALUE;
        int minFreq = Integer.MAX_VALUE;
        int maxElem = -1, minElem = -1;

        for (int i = 0; i < n; i++) {
            int count = 0;
            for (int j = 0; j < n; j++) {
                if (arr[i] == arr[j]) {
                    count++;
                }
            }
            if (count > maxFreq) {
                maxFreq = count;
                maxElem = arr[i];
            }
            if (count < minFreq) {
                minFreq = count;
                minElem = arr[i];
            }
        }

        System.out.println("Highest = " + maxElem + " (" + maxFreq + " times)");
        System.out.println("Lowest  = " + minElem + " (" + minFreq + " times)");
    }
}
```

### Time Complexity:

* **O(n²)** (nested loops).
* Not efficient for large arrays.

---

## ✅ Approach 2: HashMap (Efficient)

* Use a **HashMap** to store frequency of each element.
* Then, traverse the map to find the min and max frequency.

### Code (HashMap):

```java
import java.util.*;

public class Frequency {
    public static void main(String[] args) {
        int[] arr = {2, 3, 2, 4, 5, 3, 2, 4};

        HashMap<Integer, Integer> freqMap = new HashMap<>();

        // Count frequencies
        for (int num : arr) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        int maxFreq = Integer.MIN_VALUE, minFreq = Integer.MAX_VALUE;
        int maxElem = -1, minElem = -1;

        // Find max and min
        for (Map.Entry<Integer, Integer> entry : freqMap.entrySet()) {
            int key = entry.getKey();
            int value = entry.getValue();

            if (value > maxFreq) {
                maxFreq = value;
                maxElem = key;
            }
            if (value < minFreq) {
                minFreq = value;
                minElem = key;
            }
        }

        System.out.println("Highest = " + maxElem + " (" + maxFreq + " times)");
        System.out.println("Lowest  = " + minElem + " (" + minFreq + " times)");
    }
}
```

### Time Complexity:

* Frequency count → **O(n)**
* Finding min/max → **O(k)** where `k = unique elements`
* **Total = O(n)**

This is the **most optimal** approach.

---

## ✅ Approach 3: Sorting (Alternative)

* Sort the array.
* Traverse once and count frequencies.

### Code (Sorting):

```java
import java.util.*;

public class Frequency {
    public static void main(String[] args) {
        int[] arr = {2, 3, 2, 4, 5, 3, 2, 4};
        Arrays.sort(arr);

        int n = arr.length;
        int maxFreq = 1, minFreq = n;
        int maxElem = arr[0], minElem = arr[0];

        int count = 1;
        for (int i = 1; i < n; i++) {
            if (arr[i] == arr[i - 1]) {
                count++;
            } else {
                if (count > maxFreq) {
                    maxFreq = count;
                    maxElem = arr[i - 1];
                }
                if (count < minFreq) {
                    minFreq = count;
                    minElem = arr[i - 1];
                }
                count = 1;
            }
        }
        // last element
        if (count > maxFreq) {
            maxFreq = count;
            maxElem = arr[n - 1];
        }
        if (count < minFreq) {
            minFreq = count;
            minElem = arr[n - 1];
        }

        System.out.println("Highest = " + maxElem + " (" + maxFreq + " times)");
        System.out.println("Lowest  = " + minElem + " (" + minFreq + " times)");
    }
}
```

### Time Complexity:

* Sorting → **O(n log n)**
* Traversal → **O(n)**
* **Total = O(n log n)**

---

# 📌 Summary

* **Brute Force:** O(n²) ❌ (bad for large inputs)
* **Sorting:** O(n log n) ✅ (ok but not best)
* **HashMap:** O(n) 🚀 (best & most used in interviews)

---

👉 Do you want me to now give you a **practice problem twist** like:

* Find **top K most frequent elements**
* Or **check if two strings are anagrams using frequency count**

That will push your **frequency counting** skills to the next level 🚀. Would you like that?

## Medium-level question on platforms like LeetCode.

# 📝 Group Anagrams Problem

### Problem Statement

Given an array of strings, group the anagrams together.

👉 Two words are anagrams if they contain the same characters in the same frequency, but possibly in a different order.

---

## **Approach 1: Sorting Each Word**

* **Idea**: Sort characters of each word.
* Use the sorted string as a key in a HashMap.
* Group words with the same sorted string.

```java
import java.util.*;

public class GroupAnagramsSort {
    public static List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        for (String s : strs) {
            char[] arr = s.toCharArray();
            Arrays.sort(arr);
            String key = new String(arr);
            map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
        }
        return new ArrayList<>(map.values());
    }

    public static void main(String[] args) {
        String[] strs = {"eat","tea","tan","ate","nat","bat"};
        System.out.println(groupAnagrams(strs));
    }
}
```

### Input & Output

**Input**: `["eat","tea","tan","ate","nat","bat"]`
**Output**: `[["eat","tea","ate"],["tan","nat"],["bat"]]`

### Complexity

* Time: **O(N \* K log K)** (K = max word length for sorting)
* Space: **O(N \* K)** (storing all strings in hashmap)

---

## **Approach 2: Character Count (Frequency Vector)**

* **Idea**: Instead of sorting, use character frequency (26 letters).
* Create a 26-length array (or string) as a key.
* Faster since no sorting.

```java
import java.util.*;

public class GroupAnagramsFreq {
    public static List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        for (String s : strs) {
            int[] count = new int[26];
            for (char c : s.toCharArray()) {
                count[c - 'a']++;
            }
            String key = Arrays.toString(count);
            map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
        }
        return new ArrayList<>(map.values());
    }

    public static void main(String[] args) {
        String[] strs = {"eat","tea","tan","ate","nat","bat"};
        System.out.println(groupAnagrams(strs));
    }
}
```

### Input & Output

**Input**: `["eat","tea","tan","ate","nat","bat"]`
**Output**: `[["eat","tea","ate"],["tan","nat"],["bat"]]`

### Complexity

* Time: **O(N \* K)** (K = max word length, just counting)
* Space: **O(N \* K)** (for hashmap keys + result storage)

---


---

# ✅ Summary of Approaches

| Approach             | Key Idea                 | Time Complexity | Space Complexity | Notes                            |
| -------------------- | ------------------------ | --------------- | ---------------- | -------------------------------- |
| Sorting              | Sort each string         | O(N \* K log K) | O(N \* K)        | Simple, easy                     |
| Frequency Count      | Count chars (26 array)   | O(N \* K)       | O(N \* K)        | Faster, recommended              |

---

👉 If you’re in an **interview**, the **frequency count approach** is the most optimal and commonly expected.

Do you want me to also **draw a dry-run example step by step (with hashmap evolution)** for better visualization?

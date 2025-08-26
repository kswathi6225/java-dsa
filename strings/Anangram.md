

## ❓ Question: Check if Two Strings are Anagrams

**Problem Statement:**
Given two strings `s1` and `s2`, check whether they are **anagrams** of each other.
Two strings are anagrams if they contain the same characters with the same frequency, but possibly in a different order.

**Example:**

```
Input: s1 = "listen", s2 = "silent"  
Output: true  

Input: s1 = "hello", s2 = "world"  
Output: false
```

---

### ✅ Approach 1: Sorting

If we sort both strings, they should become identical if they are anagrams.

```java
import java.util.Arrays;

public class AnagramCheck {
    public static boolean isAnagram(String s1, String s2) {
        if (s1.length() != s2.length()) return false;
        
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        
        Arrays.sort(arr1);
        Arrays.sort(arr2);
        
        return Arrays.equals(arr1, arr2);
    }
    
    public static void main(String[] args) {
        System.out.println(isAnagram("listen", "silent")); // true
        System.out.println(isAnagram("hello", "world"));   // false
    }
}
```

⏱ Time Complexity: `O(n log n)` (due to sorting)

---

### ✅ Approach 2: Frequency Count (Better)

Count characters of both strings and compare.

```java
public class AnagramCheck {
    public static boolean isAnagram(String s1, String s2) {
        if (s1.length() != s2.length()) return false;

        int[] freq = new int[26];  // assuming lowercase a-z

        for (char c : s1.toCharArray()) {
            freq[c - 'a']++;
        }
        for (char c : s2.toCharArray()) {
            freq[c - 'a']--;
        }

        for (int f : freq) {
            if (f != 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isAnagram("listen", "silent")); // true
        System.out.println(isAnagram("race", "care"));     // true
        System.out.println(isAnagram("hello", "world"));   // false
    }
}
```

⏱ Time Complexity: `O(n)`

---

👉 Do you want me to also give the **Python version** side-by-side like last time?

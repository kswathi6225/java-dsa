Great one 👍 This is a **classic sliding window problem** often asked in interviews.
We’ll solve: **Longest Substring Without Repeating Characters**

---

### 🔹 Problem:

Given a string `s`, find the length of the **longest substring** without repeating characters.

Example:

```
Input: "abcabcbb"
Output: 3  (because "abc" is the longest substring)
```

---

### 🔹 Approach (Sliding Window + HashSet)

1. Use **two pointers (left, right)** → represent current window.
2. Expand `right` by moving through the string.
3. If character is already in window → shrink from `left`.
4. Keep track of the **maximum length** seen.

---

### 🔹 Java Code

```java
import java.util.*;

public class LongestSubstring {
    public static int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            // If char already in window, shrink window
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        String s = "abcabcbb";
        System.out.println("Input: " + s);
        int result = lengthOfLongestSubstring(s);
        System.out.println("Longest substring length = " + result);
    }
}
```

---

### 🔹 Input / Output

```
Input: abcabcbb
Output: 3
```

```
Input: pwwkew
Output: 3   (substring "wke")
```

```
Input: bbbbb
Output: 1   (substring "b")
```

---

### 🔹 Time & Space Complexity

* **Time Complexity** = O(n) → each character is visited at most twice (left & right).
* **Space Complexity** = O(min(n, charset)) → HashSet stores unique characters in window.

---

👉 Do you also want me to show you a **dry run diagram** (step by step sliding window movement) for `"abcabcbb"`?

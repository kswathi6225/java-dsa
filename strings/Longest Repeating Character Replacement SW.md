**Longest Repeating Character Replacement** (LeetCode 424).

---

## 🔹 Problem Statement

Given a string `s` and an integer `k`, you can replace **at most `k` characters** in the string.
Find the **length of the longest substring** that contains the same letter after replacements.

---

### Example 1

```
s = "AABABBA", k = 1
```

* Longest substring is `"AABA"` → replace `'B'` → `"AAAA"` → length = **4**.

---

## 🔹 Approaches

### 1. Brute Force (O(n²))

* Check every substring.
* For each substring, check if it can be converted to all same chars with ≤ `k` replacements.
* ❌ Too slow for large strings.

```java
public class LongestRepeatingCharReplacement {
    public static int characterReplacement(String s, int k) {
        int n = s.length();
        int maxLen = 0;

        // Try all substrings
        for (int start = 0; start < n; start++) {
            int[] freq = new int[26];
            int maxFreq = 0;

            for (int end = start; end < n; end++) {
                freq[s.charAt(end) - 'A']++;
                maxFreq = Math.max(maxFreq, freq[s.charAt(end) - 'A']);

                int windowLen = end - start + 1;

                // If we can convert with <= k changes
                if (windowLen - maxFreq <= k) {
                    maxLen = Math.max(maxLen, windowLen);
                }
            }
        }
        return maxLen;
    }

    public static void main(String[] args) {
        String s = "AABABBA";
        int k = 1;
        System.out.println(characterReplacement(s, k)); // Output: 4
    }
}

```

---

### 2. Sliding Window + Frequency Count (O(n))

👉 This is the efficient approach.

**Idea:**

* Use a window `[left, right]` that expands.
* Keep track of **max frequency character** inside the window.
* If window length − max frequency > `k`, shrink the window.
* Answer = max window size seen.

---

### 🔹 Code (Java)

```java
public class LongestRepeatingCharacterReplacement {
    public static int characterReplacement(String s, int k) {
        int[] count = new int[26]; // frequency of characters
        int left = 0, maxCount = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            count[s.charAt(right) - 'A']++;
            maxCount = Math.max(maxCount, count[s.charAt(right) - 'A']);

            // if replacements needed > k → shrink window
            while ((right - left + 1) - maxCount > k) {
                count[s.charAt(left) - 'A']--;
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        String s = "AABABBA";
        int k = 1;
        System.out.println(characterReplacement(s, k)); // Output: 4
    }
}
```

---

### 🔹 Dry Run (for `"AABABBA", k=1`)

* Expand window → keep track of max frequency char (`A` here).
* If window becomes invalid (needs more than `k` replacements), move `left`.
* Max length found = **4** (`AABA`).

---

✅ Time Complexity: **O(n)**
✅ Space Complexity: **O(26) = O(1)**

---

Do you want me to also show this in **Python** (since you’re practicing both Java & Python)?

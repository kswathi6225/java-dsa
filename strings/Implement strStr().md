Perfect 👌 Let’s tackle **Implement strStr()** (LeetCode 28).

---

# 📌 Problem: Implement `strStr()`

You need to find the **first occurrence** of a substring (`needle`) in a string (`haystack`).
If `needle` is not found, return `-1`.
If `needle` is an empty string, return `0`.

---

## ✅ Approach 1: Brute Force (Simple)

Check each substring of `haystack` of length `needle.length()`.

### Code (Java)

```java
public class Main {
    public static int strStr(String haystack, String needle) {
        int n = haystack.length();
        int m = needle.length();

        if (m == 0) return 0;  // empty needle

        for (int i = 0; i <= n - m; i++) {
            if (haystack.substring(i, i + m).equals(needle)) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(strStr("hello", "ll"));  // 2
        System.out.println(strStr("aaaaa", "bba")); // -1
        System.out.println(strStr("leetcode", "le")); // 0
        System.out.println(strStr("abc", "")); // 0
    }
}
```

### Complexity

* **Time:** `O((n-m+1) * m)` → Worst case `O(n*m)`
* **Space:** `O(1)`

---

## ✅ Approach 2: Optimal (KMP Algorithm – Knuth-Morris-Pratt)

⚡ Better for long strings, avoids re-checking characters.

### Code (Java)

```java
public class Main {
    public static int strStr(String haystack, String needle) {
        int n = haystack.length(), m = needle.length();
        if (m == 0) return 0;

        // Build LPS (Longest Prefix Suffix) array
        int[] lps = new int[m];
        for (int i = 1, len = 0; i < m; ) {
            if (needle.charAt(i) == needle.charAt(len)) {
                lps[i++] = ++len;
            } else if (len > 0) {
                len = lps[len - 1];
            } else {
                lps[i++] = 0;
            }
        }

        // KMP Search
        for (int i = 0, j = 0; i < n; ) {
            if (haystack.charAt(i) == needle.charAt(j)) {
                i++; j++;
                if (j == m) return i - j;
            } else if (j > 0) {
                j = lps[j - 1];
            } else {
                i++;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(strStr("hello", "ll"));     // 2
        System.out.println(strStr("aaaaa", "bba"));    // -1
        System.out.println(strStr("leetcode", "le"));  // 0
        System.out.println(strStr("mississippi", "issi")); // 1
    }
}
```

### Complexity

* **Time:** `O(n + m)`
* **Space:** `O(m)`

---

✅ For **interview**:

* Start with Brute Force.
* If interviewer asks for **efficient solution**, explain KMP.

Do you want me to **dry run KMP** on `"mississippi", "issi"` so you see how the LPS array helps?

Perfect 👍 This is **LeetCode 28: Find the Index of the First Occurrence in a String** (a.k.a. `strStr()` problem).

---

# 📌 Problem Statement

Given two strings `haystack` and `needle`, return the **index of the first occurrence** of `needle` in `haystack`.
If `needle` is not part of `haystack`, return `-1`.

---

## ✅ Example

```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0.
```

```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
```

---

## ✅ Approach 1: Brute Force

* Try every index in `haystack`.
* Compare substring with `needle`.

### Code (Java)

```java
public class Main {
    public static int strStrBrute(String haystack, String needle) {
        int n = haystack.length();
        int m = needle.length();

        for (int i = 0; i <= n - m; i++) {
            if (haystack.substring(i, i + m).equals(needle)) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(strStrBrute("sadbutsad", "sad")); // 0
        System.out.println(strStrBrute("leetcode", "leeto")); // -1
    }
}
```

⏱ **Time:** `O((n-m+1) * m)` (worst case: quadratic)
📦 **Space:** `O(1)`

---

## ✅ Approach 2: Optimal using Built-in `indexOf`

* Java’s `String.indexOf()` already implements efficient searching.

### Code (Java)

```java
public class Main {
    public static int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);
    }

    public static void main(String[] args) {
        System.out.println(strStr("sadbutsad", "sad")); // 0
        System.out.println(strStr("leetcode", "leeto")); // -1
    }
}
```

⏱ **Time:** `O(n + m)` (internally optimized with KMP-like algorithms)
📦 **Space:** `O(1)`

---

## ✅ Input & Output

```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0

Input: haystack = "leetcode", needle = "leeto"
Output: -1

Input: haystack = "mississippi", needle = "issi"
Output: 1
```

---

👉 For interviews, explain **both brute force and optimal**.
The **`indexOf` approach** is usually the best in Java.

Do you want me to also explain the **KMP algorithm** for this (manual optimal approach without built-in functions)?

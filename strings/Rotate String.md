Good question 👍 This is **LeetCode 796: Rotate String**.

---

# 📌 Problem: Rotate String

Given two strings `s` and `goal`, return `true` if and only if `s` can become `goal` after some number of **shifts**.

A **shift** means moving the **first character** of `s` to the **end**.

---

## ✅ Example

```
Input: s = "abcde", goal = "cdeab"
Output: true
Explanation: shift "abcde" → "bcdea" → "cdeab"
```

```
Input: s = "abcde", goal = "abced"
Output: false
```

---

## ✅ Approach 1: Brute Force (Try All Rotations)

* Generate all rotations of `s`.
* Check if any matches `goal`.

### Code (Java)

```java
public class Main {
    public static boolean rotateStringBrute(String s, String goal) {
        if (s.length() != goal.length()) return false;

        for (int i = 0; i < s.length(); i++) {
            String rotated = s.substring(i) + s.substring(0, i);
            if (rotated.equals(goal)) return true;
        }
        return false;
    }

    public static void main(String[] args) {
        System.out.println(rotateStringBrute("abcde", "cdeab")); // true
        System.out.println(rotateStringBrute("abcde", "abced")); // false
    }
}
```

⏱ **Time:** `O(n^2)` (substring creation & comparisons)
📦 **Space:** `O(n)`

---

## ✅ Approach 2: Optimal (String Concatenation Trick 🚀)

* If `goal` is a rotation of `s`, then `goal` must be a **substring** of `s+s`.
* Example: `"abcdeabcde"` contains `"cdeab"`.

### Code (Java)

```java
public class Main {
    public static boolean rotateString(String s, String goal) {
        return s.length() == goal.length() && (s + s).contains(goal);
    }

    public static void main(String[] args) {
        System.out.println(rotateString("abcde", "cdeab")); // true
        System.out.println(rotateString("abcde", "abced")); // false
    }
}
```

⏱ **Time:** `O(n)` (string contains check uses KMP-like under the hood)
📦 **Space:** `O(n)` (concatenated string storage)

---

## 🔍 Which is Better?

✔ Optimal **Approach 2** is preferred because it’s **cleaner & faster** than brute force.

---

Do you want me to also show how this works **step by step** for `"abcde" → "cdeab"`?

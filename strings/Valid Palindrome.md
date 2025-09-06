
# Valid Palindrome Problem

## Problem Statement
Given a string `s`, determine if it is a palindrome, considering only **alphanumeric characters** and ignoring cases.

### Example:
- Input: `"A man, a plan, a canal: Panama"`
- Output: `true`

- Input: `"race a car"`
- Output: `false`

---

## 🥉 Brute Force Approach

### Idea:
1. Convert string to lowercase.
2. Remove all non-alphanumeric characters.
3. Reverse the string and check if it equals the cleaned string.

### Java Code:
```java
public class Main {
    public static boolean isPalindromeBrute(String s) {
        // Keep only alphanumeric and lowercase
        s = s.toLowerCase().replaceAll("[^a-z0-9]", "");

        // Reverse string
        String reversed = new StringBuilder(s).reverse().toString();

        return s.equals(reversed);
    }

    public static void main(String[] args) {
        System.out.println(isPalindromeBrute("A man, a plan, a canal: Panama")); // true
        System.out.println(isPalindromeBrute("race a car")); // false
    }
}
````

### Complexity:

* **Time:** `O(n)` (building cleaned string + reversing + comparison)
* **Space:** `O(n)` (for storing reversed string)

---

## 🥈 Optimized Two-Pointer Approach

### Idea:

1. Use two pointers (`left` and `right`).
2. Skip non-alphanumeric characters.
3. Compare characters, ignoring case.
4. If mismatch → return `false`. If all match → `true`.

### Java Code:

```java
public class Main {
    public static boolean isPalindromeTwoPointer(String s) {
        int left = 0, right = s.length() - 1;

        while (left < right) {
            // Skip non-alphanumeric characters
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            // Compare ignoring case
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }

            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isPalindromeTwoPointer("A man, a plan, a canal: Panama")); // true
        System.out.println(isPalindromeTwoPointer("race a car")); // false
    }
}
```

### Complexity:

* **Time:** `O(n)` (single scan with two pointers)
* **Space:** `O(1)` (in-place comparison, no extra string storage)

---

## ✅ Conclusion

* **Brute Force:** Easier to implement but uses extra space.
* **Two Pointer:** Optimal solution with `O(1)` extra space.

```

---

Do you also want me to write the **Python version** for both brute force and two-pointer so you can compare Java & Python side by side?
```

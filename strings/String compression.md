Perfect 👍 Let’s go step by step for **String Compression** (like in LeetCode 443: *String Compression*).

### Problem:

Given a string like
👉 `"aaabbc"` → compress it as `"a3b2c1"` or `"a3b2c"` (depending on the format).

---

## 🔹 Approach 1: **Brute Force (Concatenation in loop)**

* Traverse through the string.
* For each group of repeating characters, count them.
* Append character + count to a new string.
* This approach uses **string concatenation** repeatedly → inefficient (O(n²) time).

### Example:

```java
public class StringCompressionBrute {
    public static String compress(String s) {
        String result = "";
        int i = 0;
        while (i < s.length()) {
            char ch = s.charAt(i);
            int count = 0;
            while (i < s.length() && s.charAt(i) == ch) {
                i++;
                count++;
            }
            result = result + ch + count; // concatenation
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(compress("aaabbc")); // a3b2c1
    }
}
```

---

## 🔹 Approach 2: **Better (Using StringBuilder)**

* Instead of string concatenation, use `StringBuilder` (efficient in Java).
* Reduces time complexity to **O(n)**.

```java
public class StringCompressionSB {
    public static String compress(String s) {
        StringBuilder sb = new StringBuilder();
        int i = 0;
        while (i < s.length()) {
            char ch = s.charAt(i);
            int count = 0;
            while (i < s.length() && s.charAt(i) == ch) {
                i++;
                count++;
            }
            sb.append(ch);
            sb.append(count);
        }
        return sb.toString();
    }

    public static void main(String[] args) {
        System.out.println(compress("aaabbc")); // a3b2c1
    }
}
```

---

## 🔹 Approach 3: **In-place Compression (Efficient, LeetCode Style)**

* Modify the input array of characters directly (no extra string).
* Use **two pointers**:

  * `read` → scans through string
  * `write` → writes compressed characters
* For each group:

  * Write the character
  * Write count (if > 1)

⏱ Time: O(n),
📦 Space: O(1) (in-place).

```java
public class StringCompressionInPlace {
    public static int compress(char[] chars) {
        int write = 0, read = 0;
        while (read < chars.length) {
            char ch = chars[read];
            int count = 0;
            while (read < chars.length && chars[read] == ch) {
                read++;
                count++;
            }
            chars[write++] = ch; // write char
            if (count > 1) {
                for (char c : String.valueOf(count).toCharArray()) {
                    chars[write++] = c; // write count digits
                }
            }
        }
        return write; // compressed length
    }

    public static void main(String[] args) {
        char[] arr = {'a','a','a','b','b','c'};
        int len = compress(arr);
        System.out.println(new String(arr, 0, len)); // a3b2c
    }
}
```

---

✅ **Summary of Approaches**

1. **Brute force:** Concatenate string → O(n²).
2. **Better:** Use `StringBuilder` → O(n), extra space.
3. **Efficient (In-place):** Two-pointer method → O(n), O(1) space.

---

Do you want me to **dry run** the in-place approach step by step (like I did for fruit-in-basket) so it’s crystal clear?

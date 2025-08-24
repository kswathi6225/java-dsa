Perfect 👍 Let’s solve **Palindrome Check using Recursion** in Java.

---

### Problem:

Check if a given string is palindrome (reads the same forwards and backwards) using recursion.

---

### Code (Java):

```java
public class Main {
    public static void main(String[] args) {
        String str = "madam";
        if (isPalindrome(str, 0, str.length() - 1)) {
            System.out.println(str + " is a Palindrome");
        } else {
            System.out.println(str + " is NOT a Palindrome");
        }
    }

    // Recursive function to check palindrome
    public static boolean isPalindrome(String str, int left, int right) {
        // Base case: If pointers cross, it's a palindrome
        if (left >= right) {
            return true;
        }
        // If mismatch occurs
        if (str.charAt(left) != str.charAt(right)) {
            return false;
        }
        // Recursive step
        return isPalindrome(str, left + 1, right - 1);
    }
}
```

---

### Input / Output:

**Input:** `"madam"`
**Output:**

```
madam is a Palindrome
```

**Input:** `"hello"`
**Output:**

```
hello is NOT a Palindrome
```

---

### Dry Run (for `"madam"`)

* `isPalindrome("madam", 0, 4)` → compares `m` and `m` ✅ → recurse
* `isPalindrome("madam", 1, 3)` → compares `a` and `a` ✅ → recurse
* `isPalindrome("madam", 2, 2)` → left >= right → return `true`
  → Finally returns `true` → `"madam is a Palindrome"`

---

### Time Complexity:

* Each recursive call compares **1 pair of characters**.
* Total comparisons = `n/2` (where `n` = length of string).
* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(n)` (because of recursion stack).

---

👉 Do you want me to also show the **backtracking way** (where we check after returning from recursion) for palindrome?

Great one 👍 Let’s solve **Add Strings** (LeetCode 415).

---

# 📌 Problem: Add Strings

You are given two non-negative integers `num1` and `num2` represented as strings.
Return their **sum**, also as a string.
⚡ You cannot use big integer libraries or convert the strings directly to integers.

---

## ✅ Approach 1: Brute Force (Manual Addition like School Method)

* Start from the last digit of both strings.
* Add digits + carry.
* Append result (digit by digit).
* Reverse the string at the end.

---

### Code (Java)

```java
public class Main {
    public static String addStrings(String num1, String num2) {
        int i = num1.length() - 1;
        int j = num2.length() - 1;
        int carry = 0;
        StringBuilder sb = new StringBuilder();

        while (i >= 0 || j >= 0 || carry > 0) {
            int x = (i >= 0) ? num1.charAt(i) - '0' : 0;
            int y = (j >= 0) ? num2.charAt(j) - '0' : 0;

            int sum = x + y + carry;
            sb.append(sum % 10);   // last digit
            carry = sum / 10;      // carry for next round

            i--; j--;
        }

        return sb.reverse().toString();
    }

    public static void main(String[] args) {
        System.out.println(addStrings("11", "123"));   // 134
        System.out.println(addStrings("456", "77"));   // 533
        System.out.println(addStrings("0", "0"));      // 0
        System.out.println(addStrings("99", "9"));     // 108
    }
}
```

---

## ⏱ Complexity

* **Time:** `O(max(n, m))` → linear in length of longer string
* **Space:** `O(max(n, m))` → result string storage

---

## 🟢 Input & Output Examples

```
Input: num1 = "11", num2 = "123"
Output: "134"

Input: num1 = "456", num2 = "77"
Output: "533"

Input: num1 = "0", num2 = "0"
Output: "0"

Input: num1 = "99", num2 = "9"
Output: "108"
```

---

👉 This is already **optimal** — no better approach exists since we must at least touch each digit.

Do you want me to also show how this works **step by step** for `"99" + "9"`?

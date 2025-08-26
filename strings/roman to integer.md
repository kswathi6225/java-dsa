# Roman to Integer

## Problem Statement

Convert a given **Roman numeral string** into its corresponding **integer value**.

### Roman Numerals and Their Values

```
I = 1, V = 5, X = 10, L = 50, C = 100, D = 500, M = 1000
```

Rules:

* If a smaller value appears **before** a larger one → subtract it (e.g., IV = 4).
* Otherwise → add values left to right (e.g., VI = 6).

---

## Approach 1: Using Iterative Comparison (O(n) Time, O(1) Space)

👉 Idea:

* Traverse the string from **left to right**.
* Compare each character with the **next one**.
* If current ≥ next → add current value.
* Else → subtract current from next, add result, and skip the next character.

### Code

```java
class GfG {
    // this function returns value of a Roman symbol
    static int value(char r) {
        if (r == 'I') return 1;
        if (r == 'V') return 5;
        if (r == 'X') return 10;
        if (r == 'L') return 50;
        if (r == 'C') return 100;
        if (r == 'D') return 500;
        if (r == 'M') return 1000;
        return -1;
    }

    // returns decimal value of roman numeral
    static int romanToDecimal(String s) {
        int res = 0;

        for (int i = 0; i < s.length(); i++) {
            int s1 = value(s.charAt(i));

            if (i + 1 < s.length()) {
                int s2 = value(s.charAt(i + 1));

                if (s1 >= s2) {
                    res += s1;
                } else {
                    res += (s2 - s1);
                    i++; // skip next symbol
                }
            } else {
                res += s1;
            }
        }
        return res;
    }

    public static void main(String[] args) {
        String s = "IX";
        System.out.println(romanToDecimal(s)); // Output: 9
    }
}
```

### Output

```
9
```

### Complexity

* **Time:** O(n) (scan once)
* **Space:** O(1) (no extra DS)

---

## Approach 2: Using HashMap (O(n) Time, O(1) Space)

👉 Idea:

* Store Roman symbols in a **HashMap**.
* Traverse the string.
* If current < next → subtract current from next, add result, and skip next.
* Else → add current.

### Code

```java
import java.util.HashMap;

class GfG {
    static int romanToDecimal(String s) {
        HashMap<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int res = 0;
        for (int i = 0; i < s.length(); i++) {
            if (i + 1 < s.length() && romanMap.get(s.charAt(i)) < romanMap.get(s.charAt(i + 1))) {
                res += romanMap.get(s.charAt(i + 1)) - romanMap.get(s.charAt(i));
                i++; // skip next symbol
            } else {
                res += romanMap.get(s.charAt(i));
            }
        }
        return res;
    }

    public static void main(String[] args) {
        String s = "IX";
        System.out.println(romanToDecimal(s)); // Output: 9
    }
}
```

### Output

```
9
```

### Complexity

* **Time:** O(n) (single scan)
* **Space:** O(1) (fixed map size)

---

✅ **Both approaches are efficient.**

* Approach 1 (comparison) avoids HashMap, so slightly faster.
* Approach 2 (HashMap) is cleaner and more readable.

---

Do you want me to now **dry run Approach 1 on `MCMXCIV` (1994)** step by step so you see why it works?

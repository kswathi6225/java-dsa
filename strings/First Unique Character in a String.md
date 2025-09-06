Got it 👍 Let’s simplify and only keep **two versions**:

---

# 🎯 First Unique Character in a String

---

## ✅ Brute Force Approach

### Idea:

For every character, check if it appears again in the string.

### Code (Java):

```java
public class Main {
    public static int firstUniqChar(String s) {
        int n = s.length();
        for (int i = 0; i < n; i++) {
            boolean unique = true;
            for (int j = 0; j < n; j++) {
                if (i != j && s.charAt(i) == s.charAt(j)) {
                    unique = false;
                    break;
                }
            }
            if (unique) return i;
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(firstUniqChar("leetcode"));     // 0
        System.out.println(firstUniqChar("loveleetcode")); // 2
        System.out.println(firstUniqChar("aabb"));         // -1
    }
}
```

### Complexity:

* **Time:** `O(n²)`
* **Space:** `O(1)`
  ⚠️ Too slow for large strings.

---

## ✅ Optimal Approach (Frequency Count using Array)

### Idea:

* Count frequency of characters with `int[26]`.
* Traverse again to find the first with frequency = 1.

### Code (Java):

```java
public class Main {
    public static int firstUniqChar(String s) {
        int[] freq = new int[26];

        // Count frequency
        for (char c : s.toCharArray()) {
            freq[c - 'a']++;
        }

        // Find first unique
        for (int i = 0; i < s.length(); i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(firstUniqChar("leetcode"));     // 0
        System.out.println(firstUniqChar("loveleetcode")); // 2
        System.out.println(firstUniqChar("aabb"));         // -1
    }
}
```

### Complexity:

* **Time:** `O(n)`
* **Space:** `O(1)` (fixed size 26 array)
  🚀 Most efficient solution for lowercase letters.

---

👉 So, in interview:

* If asked for **basic solution** → Brute force.
* If asked for **efficient solution** → Frequency array.

Do you want me to also give you a **step-by-step dry run of the optimal approach** on `"loveleetcode"` so you can fully see how it works?

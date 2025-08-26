
## 1️⃣ Reverse a String

### Using Inbuilt (`StringBuilder.reverse()`)

```java
public class ReverseStringInbuilt {
    public static void main(String[] args) {
        String str = "hello";
        String reversed = new StringBuilder(str).reverse().toString();
        System.out.println("Reversed: " + reversed);
    }
}
```

### Without Inbuilt (Manual Loop)

```java
public class ReverseStringManual {
    public static void main(String[] args) {
        String str = "hello";
        String reversed = "";
        for (int i = str.length() - 1; i >= 0; i--) {
            reversed += str.charAt(i);
        }
        System.out.println("Reversed: " + reversed);
    }
}
```

---

## 2️⃣ Check if String is Palindrome

### Using Inbuilt (`StringBuilder.reverse()`)

```java
public class PalindromeInbuilt {
    public static void main(String[] args) {
        String str = "madam";
        String reversed = new StringBuilder(str).reverse().toString();
        if (str.equals(reversed)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }
}
```

### Without Inbuilt (Two-pointer)

```java
public class PalindromeManual {
    public static void main(String[] args) {
        String str = "madam";
        boolean isPalindrome = true;
        int left = 0, right = str.length() - 1;

        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                isPalindrome = false;
                break;
            }
            left++;
            right--;
        }

        System.out.println(isPalindrome ? "Palindrome" : "Not Palindrome");
    }
}
```

---

## 3️⃣ Count Vowels and Consonants

### Using Inbuilt (`toLowerCase()`, `contains()`)

```java
public class CountVowelsInbuilt {
    public static void main(String[] args) {
        String str = "hello world";
        str = str.toLowerCase();
        int vowels = 0, consonants = 0;

        for (char c : str.toCharArray()) {
            if ("aeiou".contains(c + "")) {
                vowels++;
            } else if (c >= 'a' && c <= 'z') {
                consonants++;
            }
        }

        System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
    }
}
```

### Without Inbuilt (Manual check)

```java
public class CountVowelsManual {
    public static void main(String[] args) {
        String str = "hello world";
        int vowels = 0, consonants = 0;

        for (int i = 0; i < str.length(); i++) {
            char c = Character.toLowerCase(str.charAt(i));
            if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                vowels++;
            } else if (c >= 'a' && c <= 'z') {
                consonants++;
            }
        }

        System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
    }
}
```

---

## 4️⃣ Remove Spaces & Special Characters

### Using Inbuilt (`replaceAll`)

```java
public class RemoveSpacesInbuilt {
    public static void main(String[] args) {
        String str = "he@llo wor#ld!";
        String cleaned = str.replaceAll("[^a-zA-Z0-9]", "");
        System.out.println("Cleaned: " + cleaned);
    }
}
```

### Without Inbuilt (Manual loop)

```java
public class RemoveSpacesManual {
    public static void main(String[] args) {
        String str = "he@llo wor#ld!";
        StringBuilder cleaned = new StringBuilder();

        for (char c : str.toCharArray()) {
            if ((c >= 'a' && c <= 'z') || 
                (c >= 'A' && c <= 'Z') || 
                (c >= '0' && c <= '9')) {
                cleaned.append(c);
            }
        }

        System.out.println("Cleaned: " + cleaned.toString());
    }
}
```

---



## 6️⃣ Find All Permutations of a String

### Using Inbuilt (`Collections.swap` recursion helper)

```java
import java.util.*;

public class PermutationsInbuilt {
    public static void permute(String str, int l, int r) {
        if (l == r) {
            System.out.println(str);
        } else {
            for (int i = l; i <= r; i++) {
                str = swap(str, l, i);
                permute(str, l + 1, r);
                str = swap(str, l, i); 
            }
        }
    }

    public static String swap(String str, int i, int j) {
        char[] ch = str.toCharArray();
        char temp = ch[i];
        ch[i] = ch[j];
        ch[j] = temp;
        return new String(ch);
    }

    public static void main(String[] args) {
        String str = "abc";
        permute(str, 0, str.length() - 1);
    }
}
```

### Without Inbuilt (Backtracking with visited array)

```java
public class PermutationsManual {
    static void permute(String str, boolean[] used, StringBuilder out) {
        if (out.length() == str.length()) {
            System.out.println(out.toString());
            return;
        }

        for (int i = 0; i < str.length(); i++) {
            if (used[i]) continue;
            used[i] = true;
            out.append(str.charAt(i));
            permute(str, used, out);
            out.deleteCharAt(out.length() - 1);
            used[i] = false;
        }
    }

    public static void main(String[] args) {
        String str = "abc";
        boolean[] used = new boolean[str.length()];
        permute(str, used, new StringBuilder());
    }
}
```

---

## 1️⃣ Longest Substring Without Repeating Characters

```java
// Approach 1: Using HashSet (Sliding Window)
import java.util.*;
public class Main {
    public static int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int left = 0, maxLen = 0;
        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
    public static void main(String[] args) {
        System.out.println(lengthOfLongestSubstring("abcabcbb")); // Output: 3
    }
}
```

---

## 2️⃣ Longest Common Prefix

```java
// Approach 1: Sorting + Compare First & Last
import java.util.*;
public class Main {
    public static String longestCommonPrefix(String[] strs) {
        Arrays.sort(strs);
        String first = strs[0], last = strs[strs.length-1];
        int i = 0;
        while(i < first.length() && i < last.length() && first.charAt(i) == last.charAt(i)) {
            i++;
        }
        return first.substring(0, i);
    }
    public static void main(String[] args) {
        String[] arr = {"flower","flow","flight"};
        System.out.println(longestCommonPrefix(arr)); // "fl"
    }
}
```

---



## 4️⃣ Valid Parentheses

```java
// Stack Approach
import java.util.*;
public class Main {
    public static boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c=='(' || c=='{' || c=='[') stack.push(c);
            else {
                if (stack.isEmpty()) return false;
                char top = stack.pop();
                if ((c==')' && top!='(') ||
                    (c=='}' && top!='{') ||
                    (c==']' && top!='[')) return false;
            }
        }
        return stack.isEmpty();
    }
    public static void main(String[] args) {
        System.out.println(isValid("()[]{}")); // true
        System.out.println(isValid("(]"));     // false
    }
}
```

---

## 5️⃣ String Compression (like "aabb" → "a2b2")

```java
// Simple Approach
public class Main {
    public static String compress(String s) {
        StringBuilder sb = new StringBuilder();
        int count = 1;
        for (int i=1; i<=s.length(); i++) {
            if (i < s.length() && s.charAt(i)==s.charAt(i-1)) {
                count++;
            } else {
                sb.append(s.charAt(i-1)).append(count);
                count = 1;
            }
        }
        return sb.toString();
    }
    public static void main(String[] args) {
        System.out.println(compress("aabbccc")); // a2b2c3
    }
}
```

---

## 6️⃣ Minimum Window Substring

```java
// Sliding Window
import java.util.*;
public class Main {
    public static String minWindow(String s, String t) {
        Map<Character, Integer> need = new HashMap<>();
        for (char c : t.toCharArray()) need.put(c, need.getOrDefault(c, 0) + 1);
        
        int left = 0, right = 0, required = t.length();
        int minLen = Integer.MAX_VALUE, start = 0;
        
        while (right < s.length()) {
            char c = s.charAt(right);
            if (need.containsKey(c) && need.get(c) > 0) required--;
            need.put(c, need.getOrDefault(c, 0) - 1);
            right++;
            
            while (required == 0) {
                if (right - left < minLen) {
                    minLen = right - left;
                    start = left;
                }
                char l = s.charAt(left);
                need.put(l, need.getOrDefault(l, 0) + 1);
                if (need.get(l) > 0) required++;
                left++;
            }
        }
        return minLen == Integer.MAX_VALUE ? "" : s.substring(start, start+minLen);
    }
    public static void main(String[] args) {
        System.out.println(minWindow("ADOBECODEBANC", "ABC")); // "BANC"
    }
}
```

---

## 7️⃣ Edit Distance (Levenshtein Distance)

```java
// Dynamic Programming
public class Main {
    public static int minDistance(String word1, String word2) {
        int m = word1.length(), n = word2.length();
        int[][] dp = new int[m+1][n+1];
        
        for (int i=0; i<=m; i++) dp[i][0] = i;
        for (int j=0; j<=n; j++) dp[0][j] = j;
        
        for (int i=1; i<=m; i++) {
            for (int j=1; j<=n; j++) {
                if (word1.charAt(i-1) == word2.charAt(j-1))
                    dp[i][j] = dp[i-1][j-1];
                else
                    dp[i][j] = 1 + Math.min(dp[i-1][j-1], Math.min(dp[i-1][j], dp[i][j-1]));
            }
        }
        return dp[m][n];
    }
    public static void main(String[] args) {
        System.out.println(minDistance("horse", "ros")); // 3
    }
}
```

---

## 8️⃣ Check if a String is Interleaving of Two Strings

```java
// DP Approach
public class Main {
    public static boolean isInterleave(String s1, String s2, String s3) {
        if (s1.length() + s2.length() != s3.length()) return false;
        
        boolean[][] dp = new boolean[s1.length()+1][s2.length()+1];
        dp[0][0] = true;
        
        for (int i=0; i<=s1.length(); i++) {
            for (int j=0; j<=s2.length(); j++) {
                if (i > 0 && s1.charAt(i-1) == s3.charAt(i+j-1))
                    dp[i][j] |= dp[i-1][j];
                if (j > 0 && s2.charAt(j-1) == s3.charAt(i+j-1))
                    dp[i][j] |= dp[i][j-1];
            }
        }
        return dp[s1.length()][s2.length()];
    }
    public static void main(String[] args) {
        System.out.println(isInterleave("abc", "def", "adbcef")); // true
        System.out.println(isInterleave("abc", "def", "abdecf")); // false
    }
}
```




### prime-checking code

```java
public static boolean prime(int n){
    if(n <= 1){
        return false;
    }
    for(int i = 2; i * i <= n; i++){
        if(n % i == 0){
            return false;
        }
    }
    return true;
}
```

## Sieve of Eratosthenes**:

```java
import java.util.*;

public class Sieve {
    public static void sieveOfEratosthenes(int n) {
        boolean[] prime = new boolean[n+1];
        Arrays.fill(prime, true);  // assume all true initially

        prime[0] = prime[1] = false; // 0 and 1 are not prime

        for (int p = 2; p * p <= n; p++) {
            if (prime[p]) {
                // mark multiples of p as not prime
                for (int i = p * p; i <= n; i += p) {
                    prime[i] = false;
                }
            }
        }

        // print primes
        System.out.print("Prime numbers up to " + n + ": ");
        for (int i = 2; i <= n; i++) {
            if (prime[i]) {
                System.out.print(i + " ");
            }
        }
    }

    public static void main(String[] args) {
        int n = 30;
        sieveOfEratosthenes(n);
    }
}
```

---

### ✅ Output

```
Prime numbers up to 30: 2 3 5 7 11 13 17 19 23 29
```

---

⚡ **Time Complexity**: `O(n log log n)`
⚡ **Space Complexity**: `O(n)`

---

Do you want me to **dry run this Java version step by step** (like we did for Python), or should I jump to some **problems using sieve** (like count primes, segmented sieve, etc.)?


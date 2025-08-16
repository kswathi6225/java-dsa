https://www.geeksforgeeks.org/java/strings-in-java/

## convert string to char array .toCharArray()
```java
System.out.println("Length: " + str.length());
```
## convert lowercase
```java
str = str.toLowerCase();
```
## concatenation
```java
String name = "Sachin";
name = name.concat(" Tendulkar");
System.out.println(name);
```
```java
import java.util.*;
public class Main
{
	public static void main(String[] args) {
	    String str="hello world";
	    char[] word=str.toCharArray();
		System.out.println(str.toCharArray().length);
		for(char c : word){
		    System.out.println(c);
		}
	}
}
```
## output

```
11
h
e
l
l
o

w
o
r
l
d

```

### ✅ Using `Arrays.toString()` (Simple way)

```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] arr = {71, 70, 71};

        // Prints array in readable form
        System.out.println(Arrays.toString(arr));  
    }
}
```

👉 Output:

```
[71, 70, 71]
```

---

### ✅ If you specifically want curly braces `{ }`

```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] arr = {71, 70, 71};

        // Convert to string and replace square brackets with curly braces
        String result = Arrays.toString(arr).replace('[', '{').replace(']', '}');
        System.out.println(result);
    }
}
```

👉 Output:

```
{71, 70, 71}
```



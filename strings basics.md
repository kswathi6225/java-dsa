https://www.geeksforgeeks.org/java/strings-in-java/

## convert string to char array .toCharArray()
```java
System.out.println("Length: " + str.length());
```
## convert lowercase
```java
str = str.toLowerCase();
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


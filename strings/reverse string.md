```java
public class Main
{
	public static void main(String[] args) {
	
	    String name="swathi";
	    StringBuilder sb= new StringBuilder(name);
	    System.out.println(sb.reverse());
	    String reversed=" ";
	    for(int i = name.length()-1;i>0;i--){
	        reversed+=name.charAt(i);
	    }
	    System.out.println(reversed);
	}
	
}

```

### OUTPUT
```
ihtaws
ihtaws
```

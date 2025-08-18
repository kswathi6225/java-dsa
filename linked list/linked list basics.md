https://www.geeksforgeeks.org/java/linked-list-in-java/
## Basic program
```java
import java.util.*;

public class LinkedListDemo {
    public static void main(String[] args) {
        LinkedList<String> ll = new LinkedList<>();

        // Adding
        ll.add("Apple");
        ll.add("Banana");
        ll.addFirst("Mango");
        ll.addLast("Grapes");
        System.out.println("After Adding: " + ll);

        // Accessing
        System.out.println("First: " + ll.getFirst());
        System.out.println("Last: " + ll.getLast());

        // Updating
        ll.set(1, "Strawberry");
        System.out.println("After Updating: " + ll);

        // Removing
        ll.removeFirst();
        ll.removeLast();
        ll.remove("Banana");
        System.out.println("After Removing: " + ll);

        // Iterating
        System.out.print("Iterating: ");
        for (String fruit : ll) {
            System.out.print(fruit + " ");
        }
    }
}
```
## Sample Output
```java
After Adding: [Mango, Apple, Banana, Grapes]
First: Mango
Last: Grapes
After Updating: [Mango, Strawberry, Banana, Grapes]
After Removing: [Strawberry]
Iterating: Strawberry 
```

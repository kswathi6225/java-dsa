```java
import java.util.Stack;

public class Main{

    // Function to push an element at the bottom
    public static void pushAtBottom(Stack<Integer> stack, int data) {
        if (stack.isEmpty()) {
            stack.push(data);
            return;
        }

        int temp = stack.pop();
        pushAtBottom(stack, data);
        stack.push(temp);
    }

    // Function to reverse the stack
    public static void reverseStack(Stack<Integer> stack) {
        if (stack.isEmpty()) {
            return;
        }

        int temp = stack.pop();
        reverseStack(stack);
        pushAtBottom(stack, temp);
    }

    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);

        System.out.println("Original Stack (top to bottom): " + stack);

        reverseStack(stack);

        System.out.println("Reversed Stack (top to bottom): " + stack);
    }
}
```

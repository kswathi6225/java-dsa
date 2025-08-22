
```java
import java.util.ArrayList;

class Stack {
    private ArrayList<Integer> stack;

    // Constructor
    public Stack() {
        stack = new ArrayList<>();
    }

    // Push element onto stack
    public void push(int x) {
        stack.add(x);  // add at the end
        System.out.println(x + " pushed");
    }

    // Pop element from stack
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow");
            return -1;
        }
        return stack.remove(stack.size() - 1);  // remove last element
    }

    // Peek top element
    public int peek() {
        if (!isEmpty()) {
            return stack.get(stack.size() - 1);  // get last element
        }
        return -1;
    }

    // Check if stack is empty
    public boolean isEmpty() {
        return stack.size() == 0;
    }

    // Get stack size
    public int size() {
        return stack.size();
    }
}

public class Main {
    public static void main(String[] args) {
        Stack st = new Stack();

        st.push(10);
        st.push(20);
        st.push(30);

        System.out.println("Top element: " + st.peek());
        System.out.println("Removed element: " + st.pop());
        System.out.println("Stack size: " + st.size());
    }
}
```

---

### ✅ **Notes**

* `ArrayList` automatically **resizes**, so no need to worry about capacity like in the array version.
* `push()` → `add()` at the end.
* `pop()` → `remove()` last element.
* `peek()` → `get()` last element.

---

If you want, I can also show a **generic stack using ArrayList**, so it can store **any type** like `Integer`, `String`, or custom objects.

Do you want me to do that?

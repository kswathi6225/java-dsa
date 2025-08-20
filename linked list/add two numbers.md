

```java

import java.util.*;

public class Main {

    // Node class
    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // LinkedList utility class
    static class Linkedlist {
        Node head;

        // Add two numbers represented by linked lists (reverse order)
        public static Node add(Node l1, Node l2) {
            Node dummy = new Node(0);
            Node current = dummy;
            int carry = 0;

            while (l1 != null || l2 != null || carry != 0) {
                int sum = carry;
                if (l1 != null) {
                    sum += l1.data;
                    l1 = l1.next;
                }
                if (l2 != null) {
                    sum += l2.data;
                    l2 = l2.next;
                }
                carry = sum / 10;
                current.next = new Node(sum % 10);
                current = current.next;
            }

            return dummy.next;
        }

        // Print linked list
        public static void printList(Node head) {
            while (head != null) {
                System.out.print(head.data + " ");
                head = head.next;
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        // First number: 342 (stored as 2->4->3)
        Node l1 = new Node(2);
        l1.next = new Node(4);
        l1.next.next = new Node(3);

        // Second number: 465 (stored as 5->6->4)
        Node l2 = new Node(5);
        l2.next = new Node(6);
        l2.next.next = new Node(4);

        Node result = Linkedlist.add(l1, l2);

        System.out.print("Sum: ");
        Linkedlist.printList(result); // Output: 7 0 8
    }
}


```
## input
```
Enter number of digits for first number:
3
Enter digits of first number in reverse order (least significant first):
2 4 3
Enter number of digits for second number:
3
Enter digits of second number in reverse order (least significant first):
5 6 4
```

##output
```
/* 
Output:
Sum: 7 0 8 
*/
```

| Operation                       | Time Complexity | Space Complexity |
| ------------------------------- | --------------- | ---------------- |
| Create linked lists from arrays | O(n1 + n2)      | O(n1 + n2)       |
| Add two lists                   | O(max(n1, n2))  | O(max(n1, n2))   |
| Print result list               | O(max(n1, n2))  | O(1)             |
| **Overall**                     | O(n1 + n2)      | O(n1 + n2)       |


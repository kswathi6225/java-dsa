
```java
import java.util.*;

// Main class
public class Main {

    // Node class represents each element in the linked list
    static class Node{
        int data;    // stores the value of the node
        Node next;   // pointer to the next node

        Node(int data){
            this.data = data;   // initialize node value
            this.next = null;   // next initially null
        }
    }

    // Linkedlist class
    static class Linkedlist{
        Node head;   // points to the first node in the list

        // Insert at head (beginning) of the linked list
        public void insertathead(int val){
            Node newNode = new Node(val);  // create a new node
            newNode.next = head;           // link new node to current head
            head = newNode;                // update head to new node
            // Time Complexity: O(1) - constant time
            // Space Complexity: O(1) - only one extra node created
        }

        // Insert at tail (end) of the linked list
        public void insertATtail(int val){
            Node newNode = new Node(val);  // create a new node
            if(head == null){              // if list is empty
                head = newNode;            // new node becomes head
                return;
            }
            Node temp = head;
            while(temp.next != null){      // traverse to the last node
                temp = temp.next;
            }
            temp.next = newNode;           // link last node to new node
            // Time Complexity: O(n) - need to traverse list
            // Space Complexity: O(1) - only one extra node created
        }

        // Insert at a specific position (0-indexed)
        public void insertpos(int val, int pos){
            Node newNode = new Node(val);  // create new node
            if(pos == 0){                  // if inserting at head
                newNode.next = head;
                head = newNode;
                return;
            }
            
            Node temp = head;
            for(int i = 0; temp != null && i < pos - 1; i++){ // traverse to (pos-1)th node
                temp = temp.next;
            }
            if(temp == null){              // position out of bounds
                System.out.println("index out of bound");
                return;
            }
            newNode.next = temp.next;      // link new node to next node
            temp.next = newNode;           // link previous node to new node
            // Time Complexity: O(n) - traverse to position
            // Space Complexity: O(1) - only one extra node created
        }

        // Print the linked list
        public void printlist(){
            Node temp = head;
            while(temp != null){           // traverse through all nodes
                System.out.print(temp.data + "->"); // print node data
                temp = temp.next;          // move to next node
            }
            System.out.println("nul");     // indicate end of list
            // Time Complexity: O(n) - visit each node once
            // Space Complexity: O(1) - no extra space used
        }
    }

    // Main method to run linked list operations
    public static void main(String[] args) {
        Linkedlist list = new Linkedlist();   // create new linked list

        list.insertATtail(1);                 // insert 1 at tail
        list.insertATtail(2);                 // insert 2 at tail
        list.insertathead(0);                 // insert 0 at head
        list.insertpos(5, 1);                 // insert 5 at position 1

        list.printlist();                      // print the list
        // Expected Output: 0->5->1->2->nul
    }
}
```

---

### ✅ Summary of Time and Space Complexity

| Method         | Time Complexity | Space Complexity | Reason                                  |
| -------------- | --------------- | ---------------- | --------------------------------------- |
| `insertathead` | O(1)            | O(1)             | Constant time, only changing pointers   |
| `insertATtail` | O(n)            | O(1)             | Need to traverse list to find last node |
| `insertpos`    | O(n)            | O(1)             | Traverse to position in the list        |
| `printlist`    | O(n)            | O(1)             | Traverse all nodes, no extra space      |

---

If you want, I can **also add delete and search methods** with **complexities and comments**, making this a fully functional linked list tutorial.

Do you want me to do that?

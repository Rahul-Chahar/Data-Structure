# Linked List Creation
```
public class Test {
    class Node {
        int val;
        Node next;

        Node(int val) {
            this.val = val;
        }

        Node head;
        Node tail;
        int size;

        void insertAttail(int val) {
            Node node = new Node(val);
            if (head == null) {
                head = node;
                tail = node;
            } else {
                tail.next = node;
                tail = node;
            }
            size++;
        }

        void insertAtHead(int val) {
            Node node = new Node(val);
            if (head == null) head = tail = node;
            else {
                node.next = head;
                head = node;
            }
            size++;
        }

        void insert(int idx, int val) {
            if (idx == 0) {
                insertAtHead(val);
                return;
            }
            if (idx == size) {
                insertAttail(val);
                return;
            }
            if (idx > size || idx < 0) {
                System.out.println("Invalid Index");
                return;
            }
            Node temp = new Node(val);
            Node x = head;
            for (int i = 0; i < idx - 1; i++) {
                x = x.next;
            }
            temp.next = x.next;
            x.next = temp;
            size++;
        }

        int get(int idx) throws Error {
            if (idx == size - 1) return tail.val;
            if (idx >= size || idx < 0) {
                throw new Error("Invalid Index");
            }
            Node temp = head;
            for (int i = 0; i < idx; i++) {
                temp = temp.next;
            }
            return temp.val;
        }

        void set(int idx, int val) throws Error {
            if (idx == size - 1) {
                tail.val = val;
                return;
            }
            if (idx >= size || idx < 0) {
                throw new Error("Invalid Index");
            }
            Node temp = head;
            for (int i = 0; i < idx; i++) {
                temp = temp.next;
            }
            temp.val = val;
        }

        void delete(int idx) {
            if (head == null) {
                System.out.println("List is Empty");
                return;
            }
            if (idx < 0 || idx >= size) {
                System.out.println("Invalid Index");
                return;
            }
            Node temp = head;
            for (int i = 0; i < idx - 1; i++) {
                temp = temp.next;
            }
            temp.next = temp.next.next;
            size--;
        }

        void display() {
            Node temp = head;
            while (temp != null) {
                System.out.print(temp.val + " ");
                temp = temp.next;
            }
            System.out.println();
        }

    }
```
### Q-> 237 Delete Node in a Linked List
```
public class delete_Node_LinkedList_237 {
    class ListNode {
        int val;
        ListNode next;

        ListNode(int val) {
            this.val = val;
        }
    }
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```
### Q-> Middle of the LinkedList
First Approach
```
package LinkedList;

public class middle_of_the_linkedList {
    class ListNode {
        int val;
        ListNode next;

        ListNode(int val) {
            this.val = val;
        }
    }
    public ListNode middleNode(ListNode head){
     ListNode temp = head;
     int len = 0;
        while(temp != null){
            len++;
            temp = temp.next;
        }
        int mid = len/2+1;
        temp = head;
        for(int i = 1; i <= mid-1; i++){
            temp = temp.next;
        }
        return temp;
    }

    public static void main(String[] args) {
        middle_of_the_linkedList obj = new middle_of_the_linkedList();
        ListNode head = obj.new ListNode(1);
        head.next = obj.new ListNode(2);
        head.next.next = obj.new ListNode(3);
        head.next.next.next = obj.new ListNode(4);
        head.next.next.next.next = obj.new ListNode(5);
        head.next.next.next.next.next = obj.new ListNode(6);
        head.next.next.next.next.next.next = obj.new ListNode(7);
        head.next.next.next.next.next.next.next = obj.new ListNode(8);
        head.next.next.next.next.next.next.next.next = obj.new ListNode(9);
        head.next.next.next.next.next.next.next.next.next = obj.new ListNode(10);
        System.out.println(obj.middleNode(head).val);
    }
}
```
2nd Approach
```
  public ListNode middleNode(ListNode head) {
            ListNode slow = head;
            ListNode fast = head;
            while(fast != null && fast.next != null){
                slow = slow.next;
                fast = fast.next.next;
            }
            return slow;
    }
```

### Q-> Remove Nth Node from End of List
```
package LinkedList;

public class remove_Nth_node_from_end_of_List {
    class ListNode {
        int val;
        ListNode next;
        
        ListNode(int val) {
            this.val = val;
        }
    }
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode slow = head;
        ListNode fast = head;
        
        // Move fast pointer n steps ahead
        for(int i = 1; i <= n; i++){
            fast = fast.next;
        }
        if(fast == null){ // If fast is null, it means we have to remove the head node
            return head.next;
        }
        
        // Move slow and fast pointer simultaneously until fast reaches the end
        while(fast.next != null){
            slow = slow.next;
            fast = fast.next;
        }
        slow.next = slow.next.next;
        return head;
    }
    
}
```
### Q->160 Intersection of two Linked Lists
```
package LinkedList;

public class intersection_of_two_Linked_Lists {
    class ListNode {
        int val;
        ListNode next;

        ListNode(int val) {
            this.val = val;
        }
    }

    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        int lenA = 0;
        int lenB = 0;
        ListNode tempA = headA;
        ListNode tempB = headB;
        while (tempA != null) {
            lenA++;
            tempA = tempA.next;
        }
        while (tempB != null) {
            lenB++;
            tempB = tempB.next;
        }
        tempA = headA;
        tempB = headB;
        if (lenA > lenB) {
            int diff = lenA - lenB;
            for (int i = 0; i < diff; i++) {
                tempA = tempA.next;
            }
        } else {
            int diff = lenB - lenA;
            for (int i = 0; i < diff; i++) {
                tempB = tempB.next;
            }
        }
        while (tempA != tempB) {
            tempA = tempA.next;
            tempB = tempB.next;
        }
        return tempA;
    }

    public static void main(String[] args) {
        intersection_of_two_Linked_Lists obj = new intersection_of_two_Linked_Lists();
        ListNode headA = obj.new ListNode(4);
        headA.next = obj.new ListNode(1);
        headA.next.next = obj.new ListNode(8);
        headA.next.next.next = obj.new ListNode(4);
        headA.next.next.next.next = obj.new ListNode(5);

        ListNode headB = obj.new ListNode(5);
        headB.next = obj.new ListNode(0);
        headB.next.next = obj.new ListNode(1);
        headB.next.next.next = headA.next.next;

        ListNode result = obj.getIntersectionNode(headA, headB);
        System.out.println(result.val);
    }
}
```

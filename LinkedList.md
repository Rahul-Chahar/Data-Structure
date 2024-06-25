# Linked List Creation -
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

### Linked List Cycle
***Isme bas joh fast hai ouse double speed se bhadana hai jise agar cycle hai toh fast ghum kar waapas slow ke pass pouch jaaye agr aisa hua toh cycle hai***
```
package LinkedList;

public class linkedList_cycle {
    class ListNode{
        int val;
        ListNode next;
        
        ListNode(int val){
            this.val = val;
        }
    }
    public boolean hasCycle(ListNode head){
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast) return true;
        }
        return false;
    }
}
```

### Linked List Cycle II
***Isme sabe phele toh wahi same logic lagygye linked list cycle found karne waala ouske baad ham jab hame pata chal jaayega ki cycle hai toh ham ek naya variable create karegye temp naam ka joh ki head se start houga or temp or slow ek ek karke aagye bhadegye or jaha bhi dono mil jaaygye wahi se cycle start hui hai***

```
package LinkedList;

public class linkedList_cycle_II {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode detectCycle(ListNode head){
        if(head == null || head.next == null) return null;
        
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast) break;
        }
        if(fast != slow) return null;
        
        ListNode temp = head;
        while(temp != slow){
            temp = temp.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

### 83 Remove Duplicates from sorted list
***Isme a or b dou node legye b koh aagye bhadate jaaygye or ouski value compare karte jaygye a ki value se agar same hai toh b koh aage bhadate jaaygye jaise hi alag value aaygi toh a.next koh b se connect kr degye magar list ka joh last element ouske liye alg se case lihkna houga ki a.next = null ke***

```
package LinkedList;

public class remove_Duplicates_from_sorted_list {
    class Node{
        int val;
        Node next;

        Node(int val){
            this.val = val;
        }
    }
    public Node deleteDuplicates(Node head){
        if(head == null || head.next == null) return head;

        Node a = head;
        Node b = head;

        while(b != null){
            if(b.val == a.val){
                b = b.next;
            }
            else {
                a.next = b;
                a = b;
            }
        }
        a.next = null;
        return head;
    }
}
```
### 61 Rotate List
```
package LinkedList;

public class rotate_list {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode rotateRight(ListNode head, int k){
        if(head == null || head.next == null) return head;

        ListNode temp = head;
        int length = 0;

        while(temp != null){
            temp = temp.next;
            length++;
        }
        k%=length; // if k is greater than length, we need to take the modulo

        if(k == 0) return head;

        ListNode slow = head;
        ListNode fast = head;

        for(int i = 0; i< k; i++){ 
            fast = fast.next;
        }

        while(fast.next != null){ // fast.next because we need to stop at the last element
            slow = slow.next;
            fast = fast.next;
        }

        ListNode newHead = slow.next; // newHead is the new head of the list
        slow.next = null; // slow is the last element of the list
        fast.next = head; // fast is the last element of the list

        return newHead;
    }
}
```
### Merge 2 Sorted Lists
```
package LinkedList;

public class merge_2_sorted_lists {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode mergeTwoLists(ListNode l1, ListNode l2){
        ListNode dummy = new ListNode(0);
        ListNode temp = dummy;
        ListNode temp1 = l1;
        ListNode temp2 = l2;

        while(temp1 != null && temp2 != null){
            if(temp1.val <= temp2.val){
                temp.next = temp1;
                temp1 = temp1.next;
               // temp = temp.next;
            }
            else {
                temp.next = temp2;
                temp2 = temp2.next;
               // temp = temp.next;
            }
            temp = temp.next;
        }
        if(temp1 == null){
            temp.next = temp2;
        }
        else {
            temp.next = temp1;
        }
        return dummy.next;
    }
}
```
### Sort List 148 
```
package LinkedList;

public class sort_List_148 {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode merge(ListNode l1, ListNode l2){
        ListNode dummy = new ListNode(0);
        ListNode temp1 = l1;
        ListNode temp2 = l2;

        while(temp1 != null && temp2 != null){
            if(temp1.val <= temp2.val){
                dummy.next = temp1;
                temp1 = temp1.next;
            }
            else {
                dummy.next = temp2;
                temp2 = temp2.next;
            }
            dummy = dummy.next;
        }
        if(temp1 == null){
            dummy.next = temp2;
        }
        else {
            dummy.next = temp1;
        }
        return dummy.next;
    }
    public ListNode sortList(ListNode head){
        if(head == null || head.next == null) return head;
        
        ListNode firstHalf = head;
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast.next != null && fast.next.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        
        ListNode secondHalf = slow.next;
        slow.next = null;
        firstHalf = sortList(firstHalf);
        secondHalf = sortList(secondHalf);
        ListNode newHead = merge(firstHalf, secondHalf);
        return newHead;
    }
}
```

### Partition List
```
package LinkedList;

public class partition_List_86 {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode partition(ListNode head, int x){
        ListNode dummy1 = new ListNode(0);
        ListNode dummy2 = new ListNode(0);

        ListNode curr1 = dummy1;
        ListNode curr2 = dummy2;

        ListNode curr = head;

        while(curr != null){
            if(curr.val < x){
                curr1.next = curr;
                curr1 = curr1.next;
            }
            else {
                curr2.next = curr;
                curr2 = curr2.next;
            }
            curr = curr.next;
        }
        curr2.next = null;

        dummy1 = dummy1.next;
        dummy2 = dummy2.next;
        
        curr1.next = dummy2.next;
        
        return dummy1.next;

    }
}
```

### Reverse Linked List (206)
* Iterative Method

```
package LinkedList;

public class reverse_Linked_List_206 {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode reverseList(ListNode head){
        ListNode curr = head;
        ListNode prev = null;
        ListNode Next = null;
        
        while(curr != null){
            Next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = Next;
        }
        return prev;
    }
}
```

* 2nd Method (Recursive Solution)

```
public ListNode reverseList(ListNode head){
        if(head == null || head.next == null) return head;

        ListNode a = head.next;
        ListNode newHead = reverseList(a);
        a.next = head;
        head.next = null;
        return newHead;
    }
}
```
### 234 Palindrome Linked List
##### Steps
* Middle of LL
* Reverse of LL
* 2 pointer i,j
```
package LinkedList;

public class palindrome_linkedList {
    class ListNode{
        int val;
        ListNode next;

        ListNode(int val){
            this.val = val;
        }
    }
    public ListNode reverseList(ListNode head){
        if(head == null || head.next == null) return head;

        ListNode a = head.next;
        ListNode newHead = reverseList(a);
        a.next = head;
        head.next = null;
        return newHead;
    }
    public boolean isPalindrome(ListNode head){
        if(head == null || head.next == null) return true;
        
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode j = reverseList(slow);
        ListNode i = head;
        
        while(j != null){
            if(i.val != j.val) return false;
            i = i.next;
            j = j.next;
        }
        return true;
    }
}
```


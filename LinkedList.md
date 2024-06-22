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
###

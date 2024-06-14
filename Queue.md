# Queue
FIFO -> (First-In-First-Out)

```
Rear -> Push
Front -> Pop
```
eg-> Movie Ticket Counter

***Note-->  Queue ek abstract data type hai isliye ham ise directly use nahi kar skte ise use karne ke liye hame linkedlist, Arraydequeue, ArrayList jaise data structure ki jarurat houti hai***

```
package Queue;

import java.util.ArrayDeque;
import java.util.LinkedList;
import java.util.Queue;

public class implementation {
    public static void main(String[] args) {
        //Queue<Integer> que = new Queue<>(); // Queue is an interface and cannot be instantiated
        // Queue is abstract; cannot be instantiated
        Queue<Integer> que = new ArrayDeque<>();
        Queue<Integer> que2 = new LinkedList<>();
        // ArrayDeque is faster than LinkedList

        que.add(1);
        que.add(2);
        que.add(3);
        que.add(4);
        que.add(5);
        System.out.println(que);
        que.remove();
        System.out.println(que);
        que.poll();
        System.out.println(que);
        System.out.println(que.peek());
        System.out.println(que.size());
        System.out.println(que.isEmpty());
    }
}


Output
[1, 2, 3, 4, 5]
[2, 3, 4, 5]
[3, 4, 5]
3
3
false
```
### Overflow Condition
if(rear == size)

### Underflow Condition
if(rear == front)

### Q1-> Reverse the queue using a stack.

```
package Queue;

import java.util.Queue;
import java.util.Stack;

public class Reverse_queue_using_stack {
    static Queue<Integer> queue;

    static void print()
    {
        System.out.println(queue);
    }
    static void reverseQueue()
    {
        // Create a stack
        Stack<Integer> stack = new Stack<>();
        while (!queue.isEmpty()) {
            stack.add(queue.remove());

        }
        while (!stack.isEmpty()) {
            queue.add(stack.pop());

        }
    }

    public static void main(String[] args) {
        queue = new java.util.LinkedList<>();
        queue.add(56);
        queue.add(27);
        queue.add(30);
        queue.add(45);
        queue.add(85);
        queue.add(92);
        queue.add(58);
        queue.add(80);
        queue.add(90);
        queue.add(100);
        print();
        System.out.println("Reverse Queue:");
        reverseQueue();
        print();
    }
}

Output
[56, 27, 30, 45, 85, 92, 58, 80, 90, 100]
Reverse Queue:
[100, 90, 80, 58, 92, 85, 45, 30, 27, 56]
```
### Q2-> Print all the elements present in given queue only using add(), remove(), peek(), size() and extra queue
```
package Queue;

import java.util.LinkedList;
import java.util.Queue;

public class print_queue_without_using_printMethod {
    public static void main(String[] args) {
        Queue<Integer> que = new LinkedList<>();
        que.add(1);
        que.add(2);
        que.add(3);
        que.add(4);
        que.add(5);
        Queue<Integer> helper = new LinkedList<>(que);
        while(!que.isEmpty())
        {
            System.out.print(que.peek() + " ");
            helper.add(que.remove());
        }
        while (!helper.isEmpty())
        {
            que.add(helper.remove());
        }
        
    }
}

Output
1 2 3 4 5
```

### Q3-> Remove elements at odd index in a queue (use 0-based indexing)
```
package Queue;

import java.util.LinkedList;
import java.util.Queue;

public class remove_element_at_odd_index_queue {
    static Queue<Integer> que;
    static Queue<Integer> newQue;

    static void removeOdd()
    {
        newQue = new LinkedList<>();
        while (!que.isEmpty())
        {
            newQue.add(que.remove());
            if(!que.isEmpty())
            {
                que.remove();
            }
        }
        que = newQue;
    }

    public static void main(String[] args) {
        que = new LinkedList<>();
        que.add(10);
        que.add(20);
        que.add(30);
        que.add(40);
        que.add(50);
        removeOdd();
        System.out.println(que);
    }
}

Output
[10, 30, 50]
```

### Q1- Array implementation

```
package Queue;

public class array_implementation {
    public static class Que
    {
        int f = -1;
        int r = -1;
        int size = 0;
        int [] arr = new int[5];

        public void add(int val)
        {
            if(r == arr.length - 1)
            {
                System.out.println("Queue is full");
                return;
            }
            if( f == -1 && r == -1)
            {
                f = r = 0;
                arr[r] = val;
            }
            else
            {
                arr[++r] = val;
            }
            size++;
        }
        public int remove()
        {
            // Check underflow condition
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return -1;
            }
            int val = arr[f++];
            size--;
            return val;
        }
        public int peek()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return -1;
            }
            return arr[f];
        }
        public boolean isEmpty()
        {
            if(size == 0)
                return true;
            return false;
        }
        public void display()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");

            }
            else {
                for (int i = f; i <= r; i++) {
                    System.out.print(arr[i] + " ");
                }
                System.out.println();
            }
        }
        public int size()
        {
            return size;
        }
    }

    public static void main(String[] args) {
        Que que = new Que();
        que.add(1);
        que.add(2);
        que.add(3);
        que.add(4);
        que.add(5);
        que.display();
        que.remove();
        que.display();
        que.remove();
        que.display();
        System.out.println(que.peek());
        System.out.println(que.size());
        System.out.println(que.isEmpty());
    }
}


Output

1 2 3 4 5 
2 3 4 5 
3 4 5 
3
3
false
```

### Q2-> LinkedList implementation of queue
```
package Queue;

public class linkedlist_implementation_queue {
    public static class Node
    {
        int data;
        Node next;
        Node(int val)
        {
            data = val;
            next = null;
        }
    }
    public static class queueLL
    {
        Node head = null;
        Node tail = null;
        int size = 0;
        public void add(int x)
        {
            Node temp = new Node(x);
            if(size == 0)
            {
                head = tail = temp;
            }
            else
            {
                tail.next = temp;
                tail = temp;
            }
            size++;
        }
        public int peek()
        {
            if(size == 0) {
                System.out.println("Queue is empty");
                return -1;
            }
            return head.data;
        }
        public int remove()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return -1;
            }
            int val = head.data;
            head = head.next;
            size--;
            return val;
        }
        public boolean isEmpty()
        {
            if(size == 0)
                return true;
            return false;
        }
        public int size()
        {
            return size;
        }
        public void display()
        {
            Node temp = head;
            while(temp != null)
            {
                System.out.print(temp.data + " ");
                temp = temp.next;
            }
            System.out.println();
        }
    }
    public static void main(String[] args) {
        queueLL que = new queueLL();
        que.add(1);
        que.add(2);
        que.add(3);
        que.add(4);
        que.add(5);
        que.display();
        System.out.println(que.peek());
        System.out.println(que.remove());
        System.out.println(que.isEmpty());
        System.out.println(que.size());
        que.display();
    }
}

Output
1 2 3 4 5 
1
1
false
4
2 3 4 5
```
### Introduction to Deque
```
package Queue.Introduction_Deque;

public class deque {
    static class Node
    {
        int data;
        Node prev, next;

        Node(int data)
        {
            this.data = data;
            prev = next = null;
        }
    }
    static class Deque
    {
        Node front, rear;
        int size;

        Deque()
        {
            front = rear = null;
            size = 0;
        }

    boolean isEmpty()
    {
        if(size == 0)
            return true;
        return false;
    }
    int size()
    {
        return size;
    }
    void insertFront(int data)
    {
    Node newNode = new Node(data);
    if (front == null) {
        // deque is empty
        rear = front = newNode;
    }
    else {
        newNode.next = front;
        front.prev = newNode;
        front = newNode;
    }
    size++;
    }
    void insertRear(int data)
    {
        Node newNode = new Node(data);
        if (rear == null) {
            // deque is empty
            front = rear = newNode;
        }
        else {
            newNode.prev = rear;
            rear.next = newNode;
            rear = newNode;
        }
        size++;
    }
    void deleteFront()
    {
    // check for underflow
        if(size == 0)
        {
            System.out.println("Underflow");
        }
        else
        {
            Node temp = front;
            front = front.next;

            if (front == null)
                rear = null;
            else
                front.prev = null;
            size--;
        }
    }
    void deleteRear()
    {
        // check for underflow
        if(size == 0)
        {
            System.out.println("Underflow");
        }
        else
        {
            Node temp = rear;
            rear = rear.prev;

            if (rear == null)
                front = null;
            else
                rear.next = null;
            size--;
        }
    }
    int getFront()
    {
        if (size == 0) {
            System.out.println("Underflow");
            return -1;
        }
        return front.data;
    }
    int getRear()
    {
        if (size == 0) {
            System.out.println("Underflow");
            return -1;
        }
        return rear.data;
    }
    }

    public static void main(String[] args) {
        Deque dq = new Deque();
        dq.insertFront(10);
        dq.insertFront(20);
        dq.insertRear(30);
        dq.insertRear(40);
        System.out.println("Front: " + dq.getFront());
        System.out.println("Rear: " + dq.getRear());
        dq.deleteFront();
        System.out.println("Front: " + dq.getFront());
        dq.deleteRear();
        System.out.println("Rear: " + dq.getRear());
    }
}


Output
Front: 20
Rear: 40
Front: 10
Rear: 30
```

### Circular Queue
```
package Queue;

public class circular_queue {
    public static class Cqa
    {
        int front = -1;
        int rear = -1;
        int size = 0;
        int [] arr = new int[5];

        public void add(int val)
        {
            if (size == arr.length)
            {
                System.out.println("Array is full");
                return;
            }
            else if (size == 0)
            {
                front = rear = 0;
                arr[0] = val;
            }
            else if (rear < arr.length - 1)  // normal case
            {
                arr[++rear] = val;
            }
            else if(rear == arr.length-1) // rear is pointing to last index
            {
                rear = 0;
                arr[0] = val;
            }
            size++;
        }
        public int remove()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return -1;
            }
            else{
                int val = arr[front];
                if(front == arr.length-1) front = 0;
                else front++;
                size--;
                return val;

            }
        }
        public int peek()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return -1;
            }
            else return arr[front];
        }
        public void display()
        {
            if(size == 0)
            {
                System.out.println("Queue is empty");
                return;
            }
            else if (front <= rear)
            {
                for(int i = 0; i <= rear; i++)
                {
                    System.out.print(arr[i] + " ");
                }
            }
            else
            {
                // rear < front
                for(int i = front; i < arr.length; i++)
                {
                    System.out.print(arr[i] + " ");
                }
                for(int i = 0; i <= rear; i++)
                {
                    System.out.print(arr[i] + " ");
                }
            }
            System.out.println();
        }
        public boolean isEmpty()
        {
            if(size == 0) return true;
            else return false;
        }
    }

    public static void main(String[] args) {
        Cqa q = new Cqa();
        q.add(10);
        q.add(20);
        q.add(30);
        q.add(40);
        q.add(50);
        q.display();
        q.remove();
        q.display();
        q.add(60);
        q.display();
        q.remove();
        q.display();
        q.add(70);
        q.display();
    }
}

Ouput
10 20 30 40 50 
10 20 30 40 50 
20 30 40 50 60 
30 40 50 60 
30 40 50 60 70
```

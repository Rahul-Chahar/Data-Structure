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


 ### Reverse first k elements of a Queue
```
package Queue;

import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;

public class Reverse_irst_k_elements_Queue {
    public Queue<Integer> modifyQueue(Queue<Integer> q, int k) {
        // use an auxiliary stack
        Stack<Integer> st = new Stack<>();
        int n = q.size() - k;

        // we pop first k elements from queue and push them into stack
        while (k-- > 0) {
            int a = q.peek();
            q.poll();
            st.push(a);
        }

        // while stack is not empty, push the elements back into queue
        while (!st.isEmpty()) {
            int a = st.peek();
            st.pop();
            q.add(a);
        }

        // now we remove the remaining elements from queue and push them back into queue
        for (int i = 0; i < n; i++) {
            int a = q.peek();
            q.poll();
            q.add(a);
        }

        return q;
    }

    public static void main(String[] args) {
        Reverse_irst_k_elements_Queue rev = new Reverse_irst_k_elements_Queue();
        Queue<Integer> q = new LinkedList<>();
        q.add(10);
        q.add(20);
        q.add(30);
        q.add(40);
        q.add(50);
        Queue<Integer> newq = rev.modifyQueue(q, 3);
        System.out.println(newq);
    }
}


Output
[30, 20, 10, 40, 50]
```
### Q-> Implement Queue using Stack
```
package Queue;

import java.util.Stack;

public class implement_queue_using_stack {

    class MyQueue {
        Stack<Integer> input;
        Stack<Integer> output;

        public MyQueue() {
            input = new Stack<>();
            output = new Stack<>();
        }
        public void push(int x) {
            input.push(x);
        }
        public int pop() {
            peek();
            return output.pop();
        }
        public int peek() {
            if (output.isEmpty())
            {
                while (!input.isEmpty()) {
                    output.push(input.pop());
                }
            }
            return output.peek();
        }
        public boolean empty() {
            return input.isEmpty() && output.isEmpty();
        }
    }

    public static void main(String[] args) {
        implement_queue_using_stack obj = new implement_queue_using_stack();
        MyQueue obj1 = obj.new MyQueue();
        obj1.push(1);
        obj1.push(2);
        obj1.push(3);
        System.out.println(obj1.pop());
        System.out.println(obj1.peek());
        System.out.println(obj1.empty());
    } 
}


T.C = O(1) for all operations
S.C = O(N) for 2 stacks [input, output]
```
### Q-> First negative in each window of size K

   ```
package Queue;

import java.util.LinkedList;
import java.util.Queue;

public class First_negative_each_window_size_K {

    class Compute{
        public long[] printFirstNegativeInteger(long A[], int N, int K)
        {
            Queue<Integer> q = new LinkedList<>();
            long[] res = new long[N-K+1];

            for(int i=0; i<K; i++){
                if(A[i]<0){
                    q.add(i);
                }
            }
            for(int i = 0; i<N-K+1; i++)
            {
                if(q.size()!= 0 && q.peek() < i){
                    q.remove();
                }
                if(q.size()!=0 && q.peek() <= i+K-1){
                    res[i] = A[q.peek()];
                }

            }
            return res;
        }
    }

    public static void main(String[] args) {
        First_negative_each_window_size_K obj = new First_negative_each_window_size_K();
        Compute obj1 = obj.new Compute();
        long[] A = {12, -1, -7, 8, -15, 30, 16, 28};
        int N = 8;
        int K = 3;
        long[] res = obj1.printFirstNegativeInteger(A, N, K);
        for(long i: res){
            System.out.print(i + " ");
        }
    }
}

Output
-1 -1 -7 0 0 0 

T.C = O(N)
S.C = O(N)
```

### Q-> Interleave the first half of the queue with the second half

```
package Queue;

import java.util.ArrayList;
import java.util.Queue;
import java.util.Stack;

public class reorder_Queue {
    public static ArrayList<Integer> rearrangeQueue(int N, Queue<Integer> q) {
        ArrayList<Integer> res = new ArrayList<>();
        Stack<Integer> st = new Stack<>();

        // Step 1: Push the first half of the queue into the stack
        for(int i = 1; i <= N / 2; i++) {
            st.push(q.remove());
        }

        // Step 2: Enqueue the stack elements back to the queue
        while(!st.isEmpty()) {
            q.add(st.pop());
        }

        // Step 3: Move the first half of the queue to the back of the queue
        for(int i = 1; i <= N / 2; i++) {
            q.add(q.remove());
        }

        // Step 4: Again, push the first half of the queue into the stack
        for(int i = 1; i <= N / 2; i++) {
            st.push(q.remove());
        }

        // Step 5: Interleave the elements from the stack and queue
        while(!st.isEmpty()) {
            q.add(st.pop());
            q.add(q.remove());
        }

        // Collect the result
        while(!q.isEmpty()) {
            res.add(q.remove());
        }

        return res;
    }

    public static void main(String[] args) {
        Queue<Integer> q = new java.util.LinkedList<>();
        q.add(11);
        q.add(12);
        q.add(13);
        q.add(14);
        q.add(15);
        q.add(16);
        q.add(17);
        q.add(18);
        q.add(19);
        q.add(20);

        ArrayList<Integer> res = rearrangeQueue(10, q);

        for(int i : res) {
            System.out.print(i + " ");
        }
    }
}

Output
11 16 12 17 13 18 14 19 15 20

T.C = O(N)
S.C = O(N)
```


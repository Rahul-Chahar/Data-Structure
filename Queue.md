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

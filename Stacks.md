# Stack?
--> LIFO => Last in first out

* Push : To insert an element in the stack
* Pop  : To remove the topmost element
* Peek : Return top most elements but do not remove that element


```
Stack <Data_Type> st = new Stack<>();
Stack <Integer> st = new Stack<>();
```

```
import java.util.Stack;
public class basicStack{
public class void main(String args[]) {
Stack<Integer> st = new Stack<>();

st.push(1);
st.push(5);
st.push(10);
st.push(20);

// to access the first element inserted in the stack

while(st.size() > 1)
{
st.pop();
}
}
}
```

T.C = O(N)

S.C = O(N)   because we take extra space whenever we want to access the first element that all the upper data put in another space 


## Q-> Reverse a Stack
Orihinal 
* 4
* 3
* 2
* 1

Reversed
* 1
* 2
* 3
* 4

```
package Stack;

import java.util.Stack;

public class reverse_Stack {
    public static void main(String [] args){
        Stack<Integer> st_original = new Stack<>();
        st_original.push(1);
        st_original.push(2);
        st_original.push(3);
        st_original.push(4);
        System.out.println(st_original);


        Stack<Integer> st_reversed = new Stack<>();
        while(!st_original.isEmpty())
    {
            //int element = st_original.pop();
            //st_reversed.push(element);

            // OR

            st_reversed.push(st_original.pop());
        }
        System.out.println(st_reversed);
    }
}

```

T.C = O(N)

S.C = O(N)



## Q2--> Copy stack into another stack in the same order

```
package Stack;

import java.util.Stack;

public class copy_Stack_into_another_Stack_in_same_order {
    public static void main(String[] args) {
        Stack<Integer> st_original = new Stack<>();
        st_original.push(1);
        st_original.push(2);
        st_original.push(3);
        st_original.push(4);
        System.out.println(st_original);

        Stack<Integer> st_temp = new Stack<>();
        while(!st_original.isEmpty())
        {
            st_temp.push(st_original.pop());
        }

        Stack<Integer> st_final = new Stack<>();
        while(!st_temp.isEmpty())
        {
            st_final.push(st_temp.pop());
        }
        System.out.println(st_final);
    }
}
```
T.C = O(N)

S.C = O(N)


## Q3-> Display Stack
```
package Stack;

import java.util.Stack;

public class display_stack {
    public static void main(String[] args) {
        Stack<Integer> st = new Stack<>();
        st.push(1);
        st.push(2);
        st.push(3);
        st.push(4);
        System.out.println(st);
    }
}
```

## Q4->  Push element at the bottom / any index
```
package Stack;

import java.util.Stack;

public class push_element_at_bottom_any_index {
    public static void main(String[] args) {
        Stack<Integer> st = new Stack<>();
        st.push(1);
        st.push(2);
        st.push(3);
        st.push(4);
        System.out.println(st);

        int new_element = 5;
        Stack<Integer> st_temp = new Stack<>();
        while (!st.isEmpty())
        {
            st_temp.push(st.pop());
        }

        st.push(new_element);
        while(!st_temp.isEmpty())
        {
            st.push(st_temp.pop());
        }
        System.out.println(st);


    }
}
```

// Any index
```
package Stack;

import java.util.Stack;

public class any_index {
    public static void main(String[] args) {
        Stack<Integer> st = new Stack<>();
        st.push(1);
        st.push(2);
        st.push(3);
        st.push(4);
        System.out.println(st);

        int new_element = 5;
        int position = 2;

        Stack<Integer> st_temp = new Stack<>();
        while(st.size() >= position)
        {
            st_temp.push(st.pop());
        }

        // our position in original stack is empty, so we push new element at that position

        st.push(new_element);

        while(st_temp.size() > 0)
        {
            st.push(st_temp.pop());
        }

        System.out.println(st);


    }
}
```
T.C = O(N)

S.C = O(N)


## Q->5 Reverse stack recursively
```
import java.util.Stack;

public class reverse_statck_recursively {

    public static void displayReverse(Stack<Integer> st)
    {
        if(st.isEmpty())
        {
            return;
        }
        int top = st.pop();
        System.out.println(top);
        displayReverse(st);
        st.push(top); 
    }
    public static void main(String[] args) {
        Stack<Integer> st = new Stack<>();
        st.push(1);
        st.push(2);
        st.push(3);
        st.push(4);
        st.push(5);
        displayReverse(st);
    }
}
```
T.C -> O(N)

S.C -> O(N)


## Q->6  Array/ArrayList Implementation
```
public class Array_ArrayList_Implementation {
    public static class Stack{
        private int [] arr = new int[5];
        private int idx = 0;

        void push(int x){
            if(isFull()){
                System.out.println("Stack is full");
                return;
            }
            arr[idx] = x;
            idx++;
        }
        int peek(){
            if(idx == 0){
                System.out.println("Stack is empty");
                return -1;
            }
            return arr[idx-1];
        }
        int pop(){
            if(idx == 0){
                System.out.println("Stack is empty");
                return -1;
            }
            int top = arr[idx-1];
            arr[idx-1] = 0;
            idx--;
            return top;
        }
        void display(){
            for(int i = 0; i < idx; i++){
                System.out.print(arr[i] + " ");
            }
            System.out.println();
        }
        int size(){
            return idx;
        }
        boolean isEmpty(){
            if(idx == 0){
                return true;
            }
            return false;
        }
        boolean isFull(){
            if(idx == arr.length){
                return true;
            }
            return false;
        }
    }

    public static void main(String[] args) {
        Stack st = new Stack();
        st.push(1);
        st.push(2);
        st.push(3);
        st.push(4);
        st.display();
        System.out.println(st.peek());
        System.out.println(st.pop());
        st.display();
        System.out.println(st.size());
        System.out.println(st.isEmpty());
    }
}
```


## Q->7 LinkedList Implementation of Stack
```
public class LinkedList_Implementation_of_Stack {
    public static class Node
    {
        int val;
        Node next;
        Node(int val)
        {
            this.val = val;
            this.next = null;
        }
    }
    public static class Stack{
        Node head = null;
        int size = 0;
        void push(int x)
        {
            Node temp = new Node(x);
            temp.next = head;
            head = temp;
            size++;
        }
        int size()
        {
            return size;
        }
        int pop()
        {
            if(head == null)
            {
                System.out.println("Stack is empty");
                return -1;
            }
            int x = head.val;
            head = head.next;
            size--;
            return x;
        }
        int peek()
        {
            if(head == null)
            {
                System.out.println("Stack is empty");
                return -1;
            }
            int x = head.val;
            return x;
        }

        boolean isEmpty()
        {
            if(size == 0)
            {
                return true;
            }
            return false;
        }

        void display()
        {
            displayRec(head);
        }

        void displayRec(Node h)
        {
            if(h == null) return;

            displayRec(h.next);
            System.out.print(h.val + " ");
        }
    }

    public static void main(String[] args) {
        Stack st = new Stack();
        st.push(10);
        st.push(20);
        st.push(30);
        st.push(40);
        System.out.println(st.peek());
        System.out.println(st.size());
        System.out.println(st.pop());
        System.out.println(st.size());
        st.display();
        System.out.println(st.isEmpty());
    }
}
```

# Problems
### Q1-> Balanced Brackets
```
() -> True
()[]{} -> True
[(){}] -> True
][ -> False
(} -> False
(){] -> False
```

*Note -> Agar kahi bhi close bracket mil gaya hai toh ye confirm hai ki ouse phele ouska opening jarur houga agar ouska opening nahi mil raha hai mtlv gadbhad hai
for eg->
][ -> False*


#### Algo:-
* Intialise an empty stack
* Traverse the input string character by character.
* If the current char is an open bracket ( (,{,[ ) push it on the stack
* If the current char is closing bracket ( ),},} ) check the stack if the stack is empty, return false, otherwise pop the element from the stack & check if it is the matches current closing bracket. of if doesn't match return false: it is not valid parathesis


```
import java.util.Stack;

public class Balanced_Brackets {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();

        for (char c : s.toCharArray()) {
            if (c == '(')
                st.push(')');
            else if (c == '{')
                st.push('}');
            else if (c == '[')
                st.push(']');
            else if (st.isEmpty() || st.pop() != c)
                return false;
        }
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Balanced_Brackets obj = new Balanced_Brackets();
        String s = "({[]})";
        if (obj.isValid(s)) {
            System.out.println("Balanced");
        } else {
            System.out.println("Not Balanced");
    }
    }
```

T.C = O(N)

S.C = O(M)


### Q2-> Remove Consecutive Duplicates in string

```
eg->
1-> aaabbb --->  ab
2-> geeks for geeks ---> geks for geks
3-> aabccba  ---> abcba
4-> aba ---> aba
5-> aaabbbb ---> a

```

Algo-->
* Create a stack of characters
* see each character of the string one by one.
  * If the stack is not empty & character on top of the stack matches a current character, it is a duplicate pop of the character from the top of the stack.
  * Otherwise push the char on the stack.
* Create a StringBuilder & pop elements from the stack & append to the StringBuilder and reverse the StringBuilder and return the string.

```
public class remove_consecutive_Duplicates {

    public  String removeDuplicates(String s){
        Stack<Character> st = new Stack<>();
        for(char c : s.toCharArray())
        {
            if(!st.isEmpty() && st.peek() == c)
            {
                st.pop();
            }
            else {
                st.push(c);
            }
        }
        StringBuilder sb = new StringBuilder();
        while(!st.isEmpty())
        {
            sb.append(st.pop());
        }
        return sb.reverse().toString();
    }

    public static void main(String[] args) {
        remove_consecutive_Duplicates obj = new remove_consecutive_Duplicates();
        String s = "abbaca";
        System.out.println(obj.removeDuplicates(s));
    }
}
```


### Q3-> Next greater element
```
    [1,2,3,4]
Ans [3,4,4,-1]

    [7,5,8,3,5]
Ans [8,8,-1,5,-1]

```
Brute Force--:
* Initialise an answer array with all elements -1 (res)
* Run an outer loop from 0 to n-1 (i), Run an inner loop for i+1 to n-1 (j), and in each iteration if arr[j]>arr[i]  res[i] = arr[j]
* Return res array

T.C -> O(N square)
S.C -> O(1)


Optimize--:
* Create an empty stack.
* Run a loop from end to start (n-1 to 0), While the element at the top of the stack is <= the current element pop it from the stack
* Otherwise if the element at the top > current element, update the answer.
*  if the stack is empty, update ans as -1.
*  Push the current element on the stack.

```
import java.util.Stack;

public class next_greater_element {

    public static long[] nextLargestElement(long[] arr, int n)
    {
        long[] output = new long[n];
        output[n-1] = -1;

        Stack<Long> st = new Stack<>();
        st.push(arr[n-1]);

        for(int i = n-2; i>=0; i--)
        {
            while(!st.isEmpty() && st.peek() <= arr[i])
            {
                st.pop();
            }
            output[i] = st.isEmpty() ? -1 : st.peek();
            st.push(arr[i]);
        }
        return output;
    }

    public static void main(String[] args) {
        long[] arr = {1, 3, 2, 4};
        int n = arr.length;
        long[] output = nextLargestElement(arr, n);
        for(long i : output)
        {
            System.out.print(i + " ");
        }
    }
}
```
T.C = O(N)

S.C = O(N)


### Q4-> Previous greater element
```
eg-1 {10,4,2,20,40,12,30}
o/p  {-1,10,4,-1,-1,40,40}

eg-2 {10,20,30,40}
o/p  {-1,-1,-1,-1}
```
Algo->
* Create a stack
* ans[0] = -1
* push arr[0] in stack
* where seeing current element, we see the top of stack & pop element <= current element
* if stack becomes empty , ans = -1 otherwise ans = top of the stack
* Push the current element in the stack.

```
import java.util.Stack;

public class previous_greater_element {
    public static void main(String[] args){
        int[] arr ={10,4,5,12,30};

        int n = arr.length;
        prevGreater(arr, n);
    }
    public static void prevGreater(int[] arr, int n)
    {

        Stack<Integer> st = new Stack<>();
        st.push(arr[0]);
        System.out.print(-1 + " ");

        for(int i = 1; i<n; i++)
        {
            while(!st.isEmpty() && st.peek() <= arr[i])
            {
                st.pop();
            }
            if(st.isEmpty())
                System.out.print(-1 + " ");
            else
                System.out.print(st.peek() + " ");
            st.push(arr[i]);
        }
    }
}
```
T.C = O(N)

S.C = O(N)

### Q5-> Stock Span problem
```
input - {100,80,60,70,60,75,85}
Output -{1  ,1 ,1 ,2 ,1 ,4 ,6}

input - {10,4,5,90,120,80}
Output -{1 ,1,2,4 ,5  ,1}
```

Brute Force-:
* For every element being visited, traverse element on the left of it and increment the span while the element on the left side is smaller.

```
public class Main{
public static void main(String [] args){
int price [] = {10,4,5,90,120,80};
int n = price.length;
int s[] = new int[n];

calculateSpan(price, n, s);
printArray(s);
}
static void calculateSpan(int[] price, int n, int[] s)
{
s[0] = 1;
for(int j = i-1; j >= 0 && (price[i] >= price[j]); j--)
s[i]++;
}
}
static void printArray(int[] arr)
{
System.out.println(Arrays.toString(arr));
}
}
```

T.C = O(N square)

S.C = O(1)

Optimize ->
* Create a stack & push 0 in it.
* set the answer of the day 1 as 1 and run a loop
* while the stack is not empty and the price of st.top <= price of the current day, pop out the stack top
* set ans of the current day, if the stack is empty i+1, or else i-st.top()
* push the current day in the stack
* print ans

```
import java.util.Stack;
public class stock_span_Problem {
    public static int[] calculateSpan(int price[], int n)
    {
        int [] arr = new int[n];

        Stack<Integer> st = new Stack<>();
        st.push(0);
        for(int i = 0; i<n; i++)
        {
            while(!st.isEmpty() && price[i] >= price[st.peek()])
            {
                st.pop();
            }
            arr[i] = st.isEmpty() ? i+1 : i - st.peek();
            st.push(i);
        }
        return arr;
    }
    public static void main(String[] args) {
        int price[] = {10, 4, 5, 90, 120, 80};
        int n = price.length;
        int[] output = calculateSpan(price, n);
        for(int i : output)
        {
            System.out.print(i + " ");
        }
    }
}
```
T.C = O(N)

S.C = O(N)


### Q6-> Largest Rectangle in Histogram
(RSE - LSE+1)*height

Right smallest element

```
import java.util.Stack;

public class largest_rectangle_Histogram {
    public int largestRectangleArea(int [] height){
        int n = height.length;
        Stack<Integer> st = new Stack<>();

        int[] leftSmall = new int[n];
        int[] rightSmall = new int[n];

        for(int i = 0; i<n; i++)
        {
            while(!st.isEmpty() && height[st.peek()] >= height[i])
            {
                st.pop();
            }
            if(st.isEmpty())
                leftSmall[i] = 0;
            else
                leftSmall[i] = st.peek() + 1;
            st.push(i);
        }
        while (!st.isEmpty())
        {
            st.pop();
        }
        for(int i = n-1; i>=0; i--)
        {
            while(!st.isEmpty() && height[st.peek()] >= height[i])
            {
                st.pop();
            }
            if(st.isEmpty())
                rightSmall[i] = n-1;
            else
                rightSmall[i] = st.peek() - 1;
            st.push(i);
        }
        int maxArea = 0;
        for(int i = 0; i<n; i++)
        {
            maxArea = Math.max(maxArea, height[i] * (rightSmall[i] - leftSmall[i] + 1));
        }
        return maxArea;
    }
    public static void main(String[] args) {
        int[] height = {2,1,5,6,2,3};
        largest_rectangle_Histogram obj = new largest_rectangle_Histogram();
        System.out.println(obj.largestRectangleArea(height));
    }
}
```
T.C = O(N)

S.C = O(N)


### Q--> LeetCode: Decode String
```
3[a]2[bc]
aaabcbc

3[a2[c]]
accaccacc

2[a3[c2[x]]y]
2[a3[cxx]y]
2[acxxcxxcxxy]
acxxcxxcxxyacxxcxxcxxy


Finding An Optimal Solution
1-> Find the first closing bracket
2-> After that go back and find the first opening bracket

// if we get a number
push the number in numberStack

// if we get anything else than a "]"
push the character in stringStack

// if we get a "["
start popping from stringStack till "["

pop from numberStack and create a repeated string

push the repeated string in stringStack
```



### Q1-> Number of people visible in a queue
Algo-->
* You can see the next right greater element, Your next left greater element can see you
* we create a stack & push indices on the stack.
* each time we see a new element, we see the height at the index which is the top of the stack. (A)
* if A < E, the current element is taller, so we have to update ans of A by +1.  (E current element)
* & since the current element is taller, it will block all further elements for the top of a stack element, so its ans is final & we can pop it from the stack
* we keep doing this until the top of the stack index height is less than the current element.
* if stack is empty, it means we don't have any left greater element for the current element.
* if the stack is not empty, it means the current element has the next left greater element & it can see it so we need to update ans for the stack top element

```
public class Number_of_people_visible_queue {
    public int [] canSeePersonsCount(int [] heights){
        int n = heights.length;
        int [] res = new int[n];
        Stack<Integer> stack = new Stack<>();
        for(int i = 0; i < n; i++){
            while(!stack.isEmpty() && heights[stack.peek()] < heights[i]){
                res[stack.peek()]++;
                stack.pop();
            }
            if(!stack.isEmpty()){
                res[stack.peek()]++;
            }
            stack.push(i);
        }
        return res;
    }
}
```
T.C = O(N)

S.C = O(N)


### Q--> Min Stack
Approach 1: Using 2 Stacks
* Create 2 stacks -- First is the main stack, Second is the min stack for maintaining a min element
* Push(x)
  * Push x in the main stack
  * if the min stack is empty or less than the current min, we will push x in the min stack
* Pop
  * Pop the value from the main stack
  * if the value is equal to the current min, remove this value from the min stack also
* Min()->
  * If min Stack is empty return -1
  * otherwise return min-peak()
```
public class min_Stack {

    Stack<Integer> s;
    Stack<Integer> min;

    public min_Stack() {
        s = new Stack<>();
        min = new Stack<>();
    }

    public void push(int val) {
        s.push(val);
        if(min.isEmpty() ||  min.peek() >= s.peek()){
            min.push(val);
        }
    }
    public void pop() {
        if(!s.isEmpty()){
            int val = s.pop();
            if(min.peek() == val){
                min.pop();
            }
        }
    }
    public int top() {
        if(s.isEmpty()){
            return -1;
        }
        return s.peek();
    }
    public int getMin() {
        if(min.isEmpty()){
            return -1;
        }
        return min.peek();
    }
}

T.C = O(1)
S.C = O(N) + O(N)  => O(N)
```

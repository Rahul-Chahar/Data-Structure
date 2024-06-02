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

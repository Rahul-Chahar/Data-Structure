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

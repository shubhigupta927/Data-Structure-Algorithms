# Implement Stack Using Deque
```cpp
#include <bits/stdc++.h> 
class Stack
{
public:
    deque<int> dq;

    // Initialize your data structure.
    Stack()
    {
        dq;
    }

    // Pushes 'X' into the stack.
    bool push(int x)
    {
        dq.push_front(x);
        return true;
    }

    // Pops top element from Stack. Returns -1 if the stack is empty, otherwise returns the popped element.
    int pop()
    {
        if(!dq.empty()){
            int deletedElement=dq.front();
            dq.pop_front();
            return deletedElement;
        }
        return -1;
    }

    // Returns the topmost element of the stack. In case the stack is empty, it returns -1.
    int top()
    {
        if(!dq.empty()){
            return dq.front();
        }
        return -1;
    }

    // Returns true if the stack is empty, otherwise false.
    bool isEmpty()
    {
        return dq.empty();
    }

    // Returns the number of elements currently present in the stack.
    int size()
    {
        return dq.size();
    }
};
```
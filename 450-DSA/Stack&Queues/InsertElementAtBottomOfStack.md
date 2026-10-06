#  Insert An Element At Its Bottom In A Given Stack
(without using any other Data Structure)
## Recursion
```cpp
#include <bits/stdc++.h> 
 void solve(stack<int>& myStack, int x){
    if(myStack.empty()){
        myStack.push(x);
        return;
    }

    int temp=myStack.top();
    myStack.pop();
    solve(myStack, x);
    myStack.push(temp);

    return;
}

stack<int> pushAtBottom(stack<int>& myStack, int x) 
{
    solve(myStack,x);
    return myStack;
}

```
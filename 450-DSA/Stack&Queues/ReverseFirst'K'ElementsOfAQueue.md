#  Reverse the first “K” elements of a queue
## Using Stack & Iteration
```cpp
#include <bits/stdc++.h> 
void reverse(queue<int> &q,int k)
{
    if(k==0 || q.empty() || k > q.size()){
        return;
    }

    stack<int> tempStack;
    int count=0;
    while(count!=k){
        tempStack.push(q.front());
        q.pop();
        count++;
    }

    while(!tempStack.empty()){
        q.push(tempStack.top());
        tempStack.pop();
    }

    int remainingElements= q.size() - k;
    for(int i=0; i<remainingElements; i++){
        q.push(q.front());
        q.pop();
    } 
}
```

## Using Recursion
```cpp
#include <bits/stdc++.h> 
void firstReverse(queue<int> &q,int k){
    if(k==0){
        return;
    }

    int temp=q.front();
    q.pop();
    firstReverse(q, k-1);
    q.push(temp);
}

void reverse(queue<int> &q,int k)
{
    if(k==0 || q.empty() || k > q.size()){
        return;
    }

    firstReverse(q, k);
    
    int remainingElements= q.size() - k;
    for(int i=0; i<remainingElements; i++){
        q.push(q.front());
        q.pop();
    }
}
```
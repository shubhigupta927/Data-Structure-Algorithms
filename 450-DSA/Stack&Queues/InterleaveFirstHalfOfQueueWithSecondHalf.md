#   Interleave The First Half Of The Queue With The Second Half

```cpp
#include <bits/stdc++.h> 
void interLeaveQueue(queue < int > & q) {
    queue<int> tempQueue;
    int n=q.size();
    int mid=q.size()/2;

    while(mid!=0){
        tempQueue.push(q.front());
        q.pop();
        mid--;
    }

    for(int i=0; i<n/2; i++){
        q.push(tempQueue.front());
        tempQueue.pop();

        q.push(q.front());
        q.pop();
    }
}
```
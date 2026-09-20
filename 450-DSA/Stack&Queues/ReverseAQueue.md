# Reverse A Queue
## Using An Array
```cpp
#include <bits/stdc++.h> 
void reverse(queue < int > & q) {
    int n=q.size();
    int arr[n];
    for(int i=0; i<n; i++){
        arr[i]=q.front();
        q.pop();
    }

    for(int i=n-1; i>=0; i--){
        q.push(arr[i]);
    }
}
```

## Using Recursion
```cpp
#include <bits/stdc++.h> 
void reverse(queue < int > & q) {
    if(q.empty()){
        return;
    }
    int temp=q.front();
    q.pop();
    reverse(q);
    q.push(temp);
}
```

## Using Auxiliary Stack
```cpp
#include <bits/stdc++.h> 
void reverse(queue < int > & q) {
    stack<int> st;
    while(!q.empty()){
        st.push(q.front());
        q.pop();
    }

    while(!st.empty()){
        q.push(st.top());
        st.pop();
    }
}
```
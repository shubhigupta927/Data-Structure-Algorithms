# Queue Using Two Stacks
## Costly enqueue()
```cpp
#include <bits/stdc++.h> 
class Queue{
    // Stacks to be used in the operations.
    stack<int> stk1, stk2;
    
    public:
    // Enqueues 'X' into the queue. Returns true after enqueuing.
    bool enqueue(int X){
        if(stk1.size()==0){
            stk1.push(X);
        }
        else{
            while(!stk1.empty()){
                stk2.push(stk1.top());
                stk1.pop();
            }

            stk2.push(X);

            while(!stk2.empty()){
                stk1.push(stk2.top());
                stk2.pop();
            }
        }
        return true;
    }

    /*
      Dequeues top element from queue. Returns -1 if the queue is empty, 
      otherwise returns the popped element.
    */
    int dequeue(){
        if(!stk1.empty()){
            int deletedElement=stk1.top();
            stk1.pop();
            return deletedElement;
        }
        return -1;
    }
};
```

## Costly dequeue() & top()
```cpp
class myQueue {

  public:
    stack<int> stk1, stk2;

    myQueue() {
        stk1,stk2;
    }

    void enqueue(int x) {
        stk1.push(x);
    }

    void dequeue() {
        if(stk1.empty() && stk2.empty()){
            return;
        }
        
        if(stk2.empty()){
            while(!stk1.empty()){
                stk2.push(stk1.top());
                stk1.pop();
            }
        }
        
        stk2.pop();
    }

    int front() {
        if(stk1.empty() && stk2.empty()){
            return -1;
        }
        
        if(stk2.empty()){
            while(!stk1.empty()){
                stk2.push(stk1.top());
                stk1.pop();
            }
        }
        
        return stk2.top();            
    }

    int size() {
        return stk1.size() + stk2.size();
        
    }
};
```
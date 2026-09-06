# Implement Stack
## Using Array
```cpp
#include<bits/stdc++.h>
using namespace std;
class Stack {
public:
    int *stack;
    int capacity;
    int topIndex;
    Stack(int capacity) {
        this->capacity=capacity;
        stack= new int[capacity];
        topIndex = -1;
      }

    void push(int num) {
        if(isFull() != 1){
            stack[++topIndex]=num;
        }
    }

    int pop() {
        if(isEmpty() == 1){
            return -1;
        }
        else{
            int x = stack[topIndex];    //deleted element
            topIndex--;
            return x;
        }
    }
    
    int top() {
        if(isEmpty() != 1){
            return stack[topIndex];
        }
        else{
            return -1;
        }
    }
    
    int isEmpty() {
        if(topIndex==-1){
            return 1;
        }
        else{
            return 0;
        }
    }
    
    int isFull() {
        if(topIndex==capacity-1){
            return 1;
        }
        else{
            return 0;
        }
    }
    
};

```
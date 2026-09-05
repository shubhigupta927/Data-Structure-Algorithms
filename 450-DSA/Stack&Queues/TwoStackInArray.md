#   Two Stack in an Array
```cpp
#include <bits/stdc++.h> 
class TwoStack {
public:
    int *stack;
    int size;
    int top1;
    int top2;

    // Initialize TwoStack.
    TwoStack(int s) {
        stack=new int[s];
        size=s;
        top1=-1;
        top2=s;
    }
    
    // Push in stack 1.
    void push1(int num) {
        if (top1+1 == top2){
            return;
        }
        stack[++top1]=num;
    }

    // Push in stack 2.
    void push2(int num) {
        if (top2-1 == top1){
            return;
        }
        stack[--top2]=num;
    }

    // Pop from stack 1 and return popped element.
    int pop1() {
        if(top1==-1){
            return -1;
        }
        int deletedElement=stack[top1];
        top1--;
        return deletedElement;
    }

    // Pop from stack 2 and return popped element.
    int pop2() {
        if(top2==size){
            return -1;
        }
        int deletedElement=stack[top2];
        top2++;
        return deletedElement;
    }
};
```
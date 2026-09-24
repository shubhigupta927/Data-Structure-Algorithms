# Implement Circular Queue
## Using Array
```cpp
#include <bits/stdc++.h> 
class CircularQueue{
    public:
    int *queue;
    int size;
    int front;
    int rear;
    CircularQueue(int n){
        queue = new int[n];
        size =n;
        front=-1;
        rear=-1;
    }

    // Enqueues 'X' into the queue. Returns true if it gets pushed into the stack, and false otherwise.
    bool enqueue(int value){
        if(isFull()){
            return false;
        }

        if(isEmpty()){
            front=0;
            rear=0;
        }
        else{
            rear=(rear+1)%size;
        }

        queue[rear]=value;
        return true;
    }

    // Dequeues top element from queue. Returns -1 if the stack is empty, otherwise returns the popped element.
    int dequeue(){
        if(isEmpty()){
            return -1;
        }
        
        int deletedElement=queue[front];

        if(front==rear){
            front=-1;
            rear=-1;
        }
        else{
            front=(front+1)%size;
        }

        return deletedElement;
    }

    bool isEmpty(){
        return front==-1;
    }

    bool isFull(){
        return (rear+1)%size==front;
    }
};
```
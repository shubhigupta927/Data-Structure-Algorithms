# Implement Stack Using Queue
## Approach 1 - Two Queues
### Costly Push()
```cpp
class Stack {
	queue<int> q1;         //primary Data Structure
    queue<int> q2;

   public:
    Stack() {
    }

    /*----------------- Public Functions of Stack -----------------*/

    int getSize() {
        return q1.size();
    }

    bool isEmpty() {
        return q1.empty();
    }

    void push(int element) {
        swap(q1,q2);                  // copy q2 to q1

        q1.push(element);             // add element in q1
        
        while(q2.size()!=0){          // copy back to q1
            q1.push(q2.front());
            q2.pop();
        }
    }

    int pop() {
        if(!isEmpty()){
            int deletedElement = q1.front();
            q1.pop();
            return deletedElement;
        }
        return -1;
    }

    int top() {
        if(!isEmpty()){
            return q1.front();
        }
        return -1;
    }
};
```

### Costly Pop() & Top()
```cpp
class Stack {
	queue<int> q1;         //primary Data Structure
    queue<int> q2;

   public:
    Stack() {
    }

    /*----------------- Public Functions of Stack -----------------*/

    int getSize() {
        return q1.size();
    }

    bool isEmpty() {
        return q1.empty();
    }

    void push(int element) {
        q1.push(element);
    }

    int pop() {
        if(!isEmpty()){
            while(q1.size()!=1){          // copy q1 to q2
                q2.push(q1.front());
                q1.pop();
            }

            int deletedElement=q1.front();
            q1.pop();                    // pop element in q1
            
            swap(q1,q2);                 // copy back to q1

            return deletedElement;
        }
        return -1;
    }

    int top() {
        if(!isEmpty()){
            while(q1.size()!=1){          // copy q1 to q2
                q2.push(q1.front());
                q1.pop();
            }

            int topElement=q1.front();
            q2.push(q1.front());
            q1.pop();                    
            
            swap(q1,q2);                 // copy back to q1

            return topElement;        
        }
        return -1;
    }
};
```

## Approach 2 - Single Queue
```cpp
class myStack {
    queue<int> q;

  public:

    void push(int x) {
        int n=q.size();
        q.push(x);
        for(int i=0; i<n; i++){
            q.push(q.front());
            q.pop();
        }
        
    }

    void pop() {
        if(!q.empty()){
            q.pop();
        }
    }

    int top() {
        if(!q.empty()){
            return q.front();
        }
        return -1;
    }

    int size() {
        return q.size();
    }
};
```
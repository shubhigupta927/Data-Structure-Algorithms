# Sort A Stack
## Recursive Approach
```cpp
class Solution {
  public:
    void InsertAtCorrectPosition(stack<int> &st, int element){
      if(st.empty() || element>=st.top()){
              st.push(element);
              return; 
      }
      int topElement=st.top();
      st.pop();
      
      InsertAtCorrectPosition(st, element);
      
      st.push(topElement);
    }
  
  
    void sortStack(stack<int> &st) {
          if(st.empty()){
              return;
          }
          
          int topElement=st.top();
          st.pop();
          
          sortStack(st);
          
          InsertAtCorrectPosition(st, topElement);
        
    }
};

```

## Using Auxiliary Stack
```cpp
class Solution {
  public:
    void sortStack(stack<int> &st) {
        stack<int> temp;
        while(!st.empty()){
            int x = st.top();
            st.pop();
            
            //Move smaller elements back to st
            while(!temp.empty() && temp.top()<x){
                st.push(temp.top());
                temp.pop();
            }
            
            temp.push(x);
        }
        
        //Move sorted elements back to st
        while(!temp.empty()){
            st.push(temp.top());
            temp.pop();
        }
    }
};

```
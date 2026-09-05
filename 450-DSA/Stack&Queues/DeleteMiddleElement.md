# Delete middle element from stack
## Iterative Solution
```cpp
#include<bits/stdc++.h>
using namespace std;
void deleteMiddle(stack<int>&inputStack, int N){
   if(N==0){
      inputStack.pop();
      return;
   }

   int i, elementsToMove=N/2;
   stack<int> temp;

   for(i=1; i<=elementsToMove; i++){
      temp.push(inputStack.top());
      inputStack.pop();
   }

   inputStack.pop();

   for(i=1; i<=elementsToMove; i++){
      inputStack.push(temp.top());
      temp.pop();
   }
   return;
}
```

## Recursive solution
```cpp
#include <bits/stdc++.h> 
using namespace std;
void solve(stack<int>&inputStack, int count, int mid){
   if(count==mid){
      inputStack.pop();
      return;
   }
   int temp=inputStack.top();
   inputStack.pop();
   count++;
   solve(inputStack, count, mid);
   inputStack.push(temp);
}


void deleteMiddle(stack<int>&inputStack, int N){
	
   if(N==0){
      inputStack.pop();
      return;
   }

   int mid=N/2;
   int count=0;
   solve(inputStack,count, mid);
}
```
# Reverse String Using Stack
```cpp
#include<bits/stdc++.h>
using namespace std;
class Solution {
  public:
    string reverse(const string& S) {
        stack<char> inputStack;
        for(int i=0; i<S.size(); i++){
            inputStack.push( S[i] );
        }
        string reverseString;
        while(inputStack.size()!=0){
            reverseString.push_back( inputStack.top() );
            inputStack.pop();
        }
        return reverseString;
    }
};
```
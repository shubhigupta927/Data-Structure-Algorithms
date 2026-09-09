# Parenthesis Checker
```cpp
class Solution {
  public:
    bool isBalanced(string& s) {
        stack<char> st;
        for(int i=0; i<s.length(); i++){
            //push opening bracket
            if(s[i]=='('  ||  s[i]=='{' ||  s[i]=='['){ 
                st.push(s[i]);
            }
            else{ //closing
                if(st.empty()){
                    return false;
                }
                
                char ch=st.top();

                if( s[i]==')' && ch=='(' ||
                    s[i]=='}' && ch=='{' ||
                    s[i]==']' && ch=='[') {
                    st.pop();
                }
                else{ // no matck
                    return false;
                }
            }
        }
        
        return st.empty();
    }
};
```
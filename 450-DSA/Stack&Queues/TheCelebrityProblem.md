# The Celebrity Problem
## Approach 1 - Using Array

```cpp
class Solution {
  public:
    int celebrity(vector<vector<int>>& mat) {
        int n= mat.size();
        vector<int> knowsMe(n, 0);
        vector<int> iKnow(n, 0);
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                if (i!=j && mat[i][j]==1){
                    iKnow[i]++;
                    knowsMe[j]++;
                }
            }
        }
        for(int i=0; i<n; i++){
            if(iKnow[i]==0 && knowsMe[i]==n-1){
                return i;
            }
        }
        return -1;
        
    }
};
```

## Approach 2 - Using Stack
```cpp
class Solution {
  public:
    int celebrity(vector<vector<int>>& mat) {
        stack<int> stack;
        for(int i=0; i< mat.size(); i++){
            stack.push(i);
        }
        int i,j;
        while(stack.size()>1){
            i= stack.top();
            stack.pop();
            
            j=stack.top();
            stack.pop();
            
            if(mat[i][j]==1){
                stack.push(j);
            }
            else{
                stack.push(i);
            }
        }
        int celeb=stack.top();
        
        for(i=0; i<mat.size(); i++){
            if(i==celeb){
                continue;
            }
            if(mat[i][celeb]==0 || mat[celeb][i]==1){
                return -1;
            }
        }
        return celeb;
    }
};
```
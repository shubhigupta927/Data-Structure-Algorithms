# Next Smaller Element
## Brute-Force
```cpp
vector<int> nextSmallerElement(vector<int> &arr, int n)
{
    vector<int> ans(n,-1);
    for(int i=0; i<n; i++){
        for(int j=i+1; j<n; j++){
            if(arr[j] < arr[i]){
                ans[i]=arr[j];
                break;
            }
        }
    }
    return ans;
}
```

## Using Stack
```cpp
#include <stack>
vector<int> nextSmallerElement(vector<int> &arr, int n)
{
    vector<int> ans(n,-1);
    stack<int> st;
    for(int i=n-1; i>=0; i--){
        while(!st.empty() && st.top()>=arr[i]){
            st.pop();
        }
        if(!st.empty()){
            ans[i]=st.top();
        }
        st.push(arr[i]);
    }
    return ans;
}
```
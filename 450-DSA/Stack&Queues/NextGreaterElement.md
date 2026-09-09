# Next Greater Element
## Brute Force
```cpp
vector<int> nextGreaterElement(vector<int>& arr, int n)
{
	vector<int> NGE(n,-1);
	if(n==1){
		NGE[0]=-1;
		return NGE;;
	}
	for(int i=0; i<=n-1; i++){
		for(int j=i+1; j<=n-1; j++){
			if(arr[j]>arr[i]){
				NGE[i]=arr[j];
				break;
			}
		}
	}
	return NGE;
}
```

## Using Stack
```cpp
#include <bits/stdc++.h>
vector<int> nextGreaterElement(vector<int>& arr, int n)
{
	vector<int> NGE(n,-1);
	stack<int> tempStack;
	for(int i=n-1; i>=0; i--){
		while(!tempStack.empty() && tempStack.top()<=arr[i]){
			tempStack.pop();
		}
		if (tempStack.empty()){
			NGE[i]=-1;
			tempStack.push(arr[i]);
		}
		else{
			NGE[i]=tempStack.top();
			tempStack.push(arr[i]);
		}
	}
	return NGE;
}
```
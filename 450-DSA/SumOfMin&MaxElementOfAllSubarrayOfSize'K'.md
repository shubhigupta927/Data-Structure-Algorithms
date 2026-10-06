#  Sum of minimum and maximum elements of all subarrays of size “K”
## Brute - Force
```cpp
#include <bits/stdc++.h> 
long long sumOfMaxAndMin(vector<int> &nums, int n, int k) {
	long long result=0;
	int min, max;
	for(int j=0; j<n-k+1; j++){
		min=max=nums[j];		
		for(int i=j; i<j+k; i++){
			if(nums[i]<min){
				min=nums[i];
			}
			if(nums[i]>max){
				max=nums[i];
			}
		}
		result=result+min+max;
	}
	return result;
}	
```

## Sliding Window Technique + multiset
```cpp
#include <bits/stdc++.h> 
long long sumOfMaxAndMin(vector<int> &nums, int n, int k) {
	multiset<int> ms;

	//for first 'k' elements
	for(int i=0; i<k; i++){
		ms.insert(nums[i]);
	}
	long long result= *ms.begin() + *ms.rbegin(); 


	for(int i=k; i<n; i++){
		//removing previous element
		ms.erase(ms.find(nums[i-k]));

		//adding new element
		ms.insert(nums[i]);

		result += *ms.begin() + *ms.rbegin();
	}
	return result;
}	
```

## Using Two Dequeues
```cpp
#include <bits/stdc++.h> 
long long sumOfMaxAndMin(vector<int> &nums, int n, int k) {
	long long result=0;
	deque<int> minDq;
	deque<int> maxDq;
	int min, max;
	min=max=nums[0];

	for(int i=0; i<n; i++){
		//removing uneccesary elements
		while(!minDq.empty() && nums[minDq.back()]>=nums[i]){
			minDq.pop_back();
		}
		while(!maxDq.empty() && nums[maxDq.back()]<=nums[i]){
			maxDq.pop_back();
		}

		//adding idices of new element
		minDq.push_back(i);
		maxDq.push_back(i);

		//removing element outside current window
		while(!minDq.empty() && minDq.front()==i-k){
			minDq.pop_front();
		}
		while(!maxDq.empty() &&maxDq.front()==i-k){
			maxDq.pop_front();
		}

		//if window is complete
		if(i >= k-1){
			min = nums[minDq.front()];
			max = nums[maxDq.front()];
			result+= min+max;
		}
	}

	return result;
}	
```
#  First unique character in a string
## Brute - Force
```cpp
#include <bits/stdc++.h> 
int firstUniqueCharacter(string s , int n) {
	int position=-1;
	bool found;
	for(int i=1; i<=s.size(); i++){
		found=false;
		for(int j=1; j<=s.size(); j++){
			if(s[j-1]==s[i-1] && i!=j){
				found=true;
				break;
			}
		}
		if(!found){
			position=i;
			break;
		}
	}
	return position;
}
```

##
```cpp

```
## 📁 Assignments Overview

<details>
<summary> Assignment 1: STL</summary>  

**Explanations:**

**Problem 2**  
I have encountered a very similar problem in my ESC111 course.
In that lab, I have prepared a solution which uses recursion but have a time complexity O(2^n). But after the lab, I learned an optimised DP solution which my friend explained me.    
First, I created a vector array 'dp' of size n, initializing all its elements with 1.  
(Here, dp[i] represents the length of longest increasing subsequence till i'th element.)  
Then, implemented a nested loop of variables i (from 0 to n-1) and j (from 0 to i-1).  
Then, I checked whether jth element is less than ith element — if no, then continue; if yes, then dp[i] will be maximum of dp[i] or dp[j] + 1.  
The above line is little complicated, let's break it step by step:  
dp[i] represents the current longest increasing subsequence (till the ith and jth iteration), same with dp[j].  
As a[j] < a[i], we get an increasing sequence till jth element(dp[j]) + the i'th element.  
`max(dp[i], dp[j]+1)` means if we already have a subsequence dp[i] larger than dp[j]+1, we will not take the dp[j]+1 sequence and continue with the dp[i] sequence.

**Example**  
Consider the array `1 9 2 3 4 5` — the above solution also helps to skip some elements which are eligible but too big to fit.  
If we take the sequence `(1, 9)`, we can't take any further element.  
But if we skip 9 and build the sequence `(1, 2, 3, 4, 5)`, it is the longest possible subsequence, and the above solution considers it.  
Lastly, I initialized the variable `ans` with the maximum element of the `dp` array.

<details>
<summary>Code :-</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
   int n;
   cin >> n;
   vector <int> arr(n);
   for(int i = 0; i < n; i++){
      cin >> arr[i];
   }
   
   vector <int> dp(n,1);
   for(int i = 0; i < n; i++){
      for(int j = 0; j < i; j++){
        if(arr[j] < arr[i]){
          dp[i] = max(dp[j] + 1, dp[i]);
      }
   }  
   }

   int ans = *max_element(dp.begin(),dp.end());
   cout << ans << endl;
   return 0;
}
```
</details>
</details>

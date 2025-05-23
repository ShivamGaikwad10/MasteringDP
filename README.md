 Assignment Submissions

## 📁 Assignments Overview

### Assignment 1: [Assignment Title]
**Objective:**  
Brief description of what the assignment aims to accomplish.

**Files:**
- `assignment1.py`: Short description of what the script does.
- `data.csv`: Optional description if applicable.

**Explanations:**

**Problem 2** :  
I have encountered a very similar problem in my ESC111 course. In that lab, I have prepared a solution which uses recursion but have a time complexity O(2^n). But after the lab, I learned a optimised DP solution which my friend explained me.  
You can view the file attached for my code.  
First, I create a vector array dp of size n, initializing all it's elements with 1. (Here, dp[i] represents the length longest increasing subsequence till i'th element.)  
Then, implemented a nested loop of variables i(from 0 to n-1) and j(from 0 to i-1).  
Then, I checked that whether jth element is less than ith element, if no then continue, if yes then dp[i] will be maximum of dp[i] or dp[j] + 1.  
The above line is little complicated, let's break it step by step, d[i] represents the current longest increasing subsequence (till the ith and jth iteration), same with dp[j]. As a[j] < a[i], we get a increasing sequence till jth element(dp[j]) + the i'th element. Maximum(dp[i],dp[j]+1) represents, if we already have a subsequence(dp[i]) larger than dp[j]+1, we will not take it.  

**Example:**  
Consider the array 1 9 2 3 4 5, the above solution also helps to skips some elements which are elgible but too big to fit.  
if we take the sequence (1,9), we can't take any further element, but if we skip 9 and build a sequence (1,2,3,4,5), it is the longest possible subsequence and the above solution considers it.  
Lastly i intialized the variable ans with 0 and took the maximum of the
---

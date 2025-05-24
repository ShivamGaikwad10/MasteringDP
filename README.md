## 📁 Assignments Overview

<details>  
   
<summary> Assignment 1: STL</summary>  

**Explanations:**  

**Problem 1**  
I was unable to find logic for maximising payoff value. So, I am submitting my partial code.

<details>
<summary>Code :-</summary>
  
  ```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int funds = 0, profit = 0;
    int p; cin >> p;
    int k; cin >> k;
    unordered_map <int,int> Cost, Sale, quantity_left;
    vector <int> product_id(p);
    for(int i = 0; i < p; i++) cin >> product_id[i];
    for(int i = 0; i < p; i++){
        quantity_left[product_id[i]] = k;
    }
    for(int i = 0; i < p; i++){
        int cost;
        cin >> cost;
        Cost[product_id[i]] = cost;
    }
    for(int i = 0; i < p; i++){
        int sale;
        cin >> sale;
        Sale[product_id[i]] = sale;
    }
    int n;
    cin >> n;
    for(int i = 0; i < n; i++){
        int budget;
        cin >> budget;
        int m;
        cin >> m;
        vector < pair< pair<int,int>,int > > query(m);
        for(int j = 0; j < m; j++){
        int product, quantity, payoff;
        cin >> product >> quantity >> payoff;
        query[j] = {{product, quantity}, payoff};
        }
    }
      return 0;
}
```
</details>  
-  -  -  -  -  -  -  -  -  -  -  -  -  -   

  
**Problem 2 :**     

  ## Explanation of the Solution

- I have encountered a very similar problem in my ESC112 course. In that lab, I prepared a solution which uses recursion but has a time complexity of **O(2^n)**.
  - But after the lab, I learned an optimized **DP solution** which was mind blowing.

- **Steps:**
  - First, I created a vector array **'dp'** of size **n**, initializing all its elements with **1**.
    - (Here, **dp[i]** represents the length of the longest increasing subsequence till the **i'th element**.)
  - Then, I implemented a nested loop of variables **i** (from 0 to n-1) and **j** (from 0 to i-1).
  - Then, I checked whether the **jth element** is less than the **ith element**:
    - If **no**, then continue.
    - If **yes**, then **dp[i]** will be the maximum of **dp[i]** or **dp[j] + 1**.

- **Breaking Down the Logic:**
  - The above lines are little complicated, so let's break it step by step:
    - **dp[i]** represents the current longest increasing subsequence (till the **ith** and **jth** iteration), same with **dp[j]**.
    - As **a[j] < a[i]**, we get an increasing sequence till the **jth** element (**dp[j]**) + the **i'th** element.
    - **max(dp[i], dp[j]+1)** means if we already have a subsequence **dp[i]** larger than **dp[j]+1**, we will not take the **dp[j]+1** sequence and continue with the **dp[i]** sequence.


**Example :-**  
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
   - - - - -   
   
**Problem 3 :**  
     I am not aware about any sorting techniques that runs at O(n), but I know a sorting technique which is efficient and runs in O(nlog(n)) time complexity which
is merge sort.    
Sorry I coudn't think about any technique running at O(n) :( .  
## Merge Sort Explanation

- **Merge sort** is a technique which halves the array repeatedly until the size of each array is not 1.
  - After this, we **merge** the halved sorted arrays in a manner such that the merged array is also sorted.

- **Merging Process:**
  - Merging is done by comparing the elemts of the both the arrays which are to be merged.
    
- **Time Complexity Breakdown:**
  - The array is halved **log(n)** times, where **n** is the number of elements.
  - In each of these steps, the merging operation takes **O(n)** time to combine the sub-arrays.
  - Therefore, the overall time complexity is **O(n log n)**.

<details>
   <summary>Self Written Merge Sort Code:-</summary>  
   
```cpp
#include <bits/stdc++.h>   
using namespace std;  

void Merge(vector <int>& arr, int start, int mid, int end){
        vector <int> temp;
        int i = start, j = mid + 1;
        while(i < mid + 1 && j < end + 1){
           if(arr[i] > arr[j]){
            temp.push_back(arr[j]);
            j++;
           }else{
            temp.push_back(arr[i]);
            i++;
           }
        }
        while(i < mid + 1){
            temp.push_back(arr[i]);
            i++;
        }
        while(j < end + 1){
            temp.push_back(arr[j]);
            j++;
        }
     for(int k = start; k <= end; k++){
        arr[k] = temp[k-start];
    }
}
void MergeSort(vector <int>& arr, int start, int end){
          if(start == end){
            return;
          }
          int mid = (start + end)/2;
          MergeSort(arr,start,mid);  
          MergeSort(arr,mid+1,end);  
          Merge(arr,start,mid,end);  
}
int main() {
    int n;
    cin >> n;
    vector <int> arr(n);
    for(int i = 0; i < n; i++){
        cin >> arr[i];
    }
    MergeSort(arr,0,n-1);
     for(int i = 0; i < n; i++){
        cout << arr[i] << " ";
    }
    return 0;
}
```
</details>
</details>

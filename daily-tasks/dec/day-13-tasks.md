---
description: 'Date : 13 December , 2020'
---

# Day 13 : Tasks

## Technical

Given the following prefix expression: \* + 3 + 3 ↑ 3 + 3 3 3   
What is the value of the prefix expression?  
a\) 2178  
b\) 2199  
c\) 2205  
d\) 2232

{% hint style="success" %}
We have prefix expression:  
3 + 3 ↑ 3 + 3 3 3  
= \* + 3 + 3 ↑ 3 6 3  
= \* + 3 + 3 729 3  
= \* + 3 732 3  
= \* 735 3  
= 2205  
So, option \(C\) is correct
{% endhint %}



## Coding

Given N bags, each bag contains Bi chocolates. There are a kid and a magician. In one unit of time, the kid chooses random bag i, eats Bi chocolates, then the magician fills the ith bag with floor\(Bi/2\) chocolates.  
Find the maximum number of chocolates that kid can eat in A units of time.  
_NOTE:_  
floor\(\) function returns the largest integer less than or equal to a given number.   
Return your answer modulo 10^9+7

_Input Format_   
First argument is an integer A. Second argument is an integer array B of size N.

_Output Format_   
Return an integer denoting the maximum number of chocolates that kid can eat in A units of time.

**Example Input**   
_Input 1:_  
A = 3 B = \[6, 5\]   
_Input 2:_  
A = 5  B = \[2, 4, 6, 8, 10\]

**Example Output**   
_Output 1:_  
14  
_Output 2:_  
33

**Example Explanation**   
_Explanation 1:_  
At t = 1 kid eats 6 chocolates from bag 0, and the bag gets filled by 3 chocolates.   
At t = 2 kid eats 5 chocolates from bag 1, and the bag gets filled by 2 chocolates.   
At t = 3 kid eats 3 chocolates from bag 0, and the bag gets filled by 1 chocolate.   
so, total number of chocolates eaten are 6 + 5 + 3 = 14

### Solution

```cpp
long long int mod = 1000000007;
int Solution::nchoc(int A, vector<int> &B) {
	int N = B.size();
	int K = A;
	long long int ans = 0;
	priority_queue<int> heap(B.begin(),B.end());
	while(K--){
		long long int max_elem = heap.top();
		ans += max_elem;
		ans = ans % mod;
		heap.pop();
		heap.push((int)(max_elem/2));
	}   
	return ans;
}
```


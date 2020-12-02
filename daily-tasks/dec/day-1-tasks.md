---
description: 'Date :1 December 2020'
---

# Day 1 : Tasks

## Aptitude

A is the son of B, C.  B's sister has a son D and a daughter E. F is the maternal uncle of D.  How is E related to F? 

1. Sister
2. Niece
3. Wife
4. Daughter

{% hint style="success" %}
**Ans:** Niece

E is the daughter of C and D is the son of C. So, F, who is the maternal uncle of D, is also the maternal uncle of E. Thus, E is the niece of F.
{% endhint %}

## Technical

Identify the scheduling technique in which a process retains the CPU until the process is terminated.

1. Round Robin scheduling
2. Cascading scheduling
3. Preemptive scheduling
4. Non-preemptive scheduling

{% hint style="success" %}
**Ans:** Non-preemptive Scheduling
{% endhint %}

## Coding Question

Layers are a popular feature in art software. Think of each layer as a transparent sheet with something drawn on it. The finished art piece is made by arranging all the layers in some order, combining them into one layer, and then viewing it from the top.

You have n layers arranged in order. Each layer has a beauty value b\[i\].

In one step, you can combine any two adjacent layers into one layer - i.e., choose i such that i + 1 &lt; current number of layers, then combine layers i and i + 1 \(0-indexed\). The beauty value of the new layer becomes the sum of the beauty values of the old layers - the old layers vanish and the new layer occupies the gap. However, for the software, some layers are harder to combine than others, which means it takes more time.

Combining layers of beauties b1 and b2 takes \(b1 + b2\) / \(abs\(b1 - b2\) + 1\) \(integer division\) seconds.

After n - 1 such steps, you will be left with the finished piece. Find the minimum time \(in seconds\) required to achieve this.

**`Input:`**

```cpp
1 3 3 5 8 
```

 

**`Output:`** 

```cpp
4
```

**`Explanation:`**There are two possible ways to combine these layers - Combine layers 0 and 1 first, and then combine the new layer with layer 2. \(0-indexed\) Combining layers 0 and 1 takes \(3 + 5\) / 3 seconds, i.e, 2 seconds. Combining the resultant layer with layer 2 takes \(8 + 8\) / 1, i.e, 16 seconds.

Therefore this approach takes 18 seconds in total. The other way is combining layers 1 and 2 first, then combining this result with layer 0. This approach takes 4 seconds in total, which is the minimum time possible to combine all layers.

### Solution:

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

int main(){
 	int t; cin>>t;
  	assert(t > 0 and t <=  5);
  	int tot = 0;
  	while(t--){
		int n; cin>>n;
	  	assert(n >= 1 and n <= 300);
	  	tot += n;
	  	ll b[n];
	  	for(int i=0;i<n;i++){ 
		  	cin>>b[i];
		  	assert(b[i] >= 1 and b[i] <= 1000000000);
		}
	  	ll dp[n][n];
	  	memset(dp, -1, sizeof dp);
	  	ll pb[n];
	  	pb[0] = b[0];
	  	for(int i=1;i<n;i++) pb[i] = pb[i-1]+b[i];
	  	for(int i=0;i<n;i++) dp[i][i] = 0;
	  	for(int i=1;i<n;i++) dp[i-1][i] = (b[i-1]+b[i])/(abs(b[i]-b[i-1])+1);
	  	for(int len = 2; len < n; len++){
			for(int i=0;i<n-len;i++){
				int j = i+len;
			  	ll here = 1e15;
			  	for(int k=i;k<j;k++){
				  	ll b1 = pb[k] - (i>0?pb[i-1]:0);
				  	ll b2 = pb[j] - pb[k];
					here = min(here, dp[i][k]+dp[k+1][j] + (b1+b2)/(abs(b1-b2)+1));
				}
			  	dp[i][j] = here;
			}
		}
	  	cout<<dp[0][n-1]<<'\n';
  	}
  	assert(tot <= 300);
}
```

### Explanation for the above Code:

{% hint style="success" %}
Given an array b, we should find the minimum time taken to "combine" its elements into one element in n - 1 steps. This is a dynamic programming problem. We need to find the minimum time required to combine any subarray of b. For any subarray, the minimum time taken to combine it entirely, will depend on its own subarrays. Intuitively, we must look at every way to partition this subarray into two non-overlapping subarrays - left\[\] and right\[\]. The minimum time to combine the original subarray is the sum of the minimum times taken to combine left and right, plus the time taken to combine the combined, final element of left and the combined, final element of right - for all possible lefts and rights. We define dp\[i\]\[j\] as the minimum time required to combine the subarray b\[i\] to b\[j\]. Let's define f\(i, j\) as the given combine-time function of two layers - f\(i, j\) = \(i + j\) / \(abs\(i - j\) + 1\) \(integer division\) We can now find dp\[i\]\[j\] as follows: dp\[i\]\[j\] = min\(dp\[i\]\[k\] + dp\[k + 1\]\[j\] + f\(sum\(i, k\), sum\(k + 1, j\)\)\), i ≤ k &lt; j sum\(i, j\) represents the sum of elements i to j in the array b. We see that calculating dp\[i\]\[j\] takes O\(n\) iterations, as we iterate from i to j. At each iteration, we call sum\(i, j\), and so we need an efficient way to find it. For this, we use prefix-sums - prefixSum\[i\] gives the sum of elements 0 to i of array b. We calculate prefixSum\[i\] as b\[i\] + prefixSum\[i - 1\] if i ≥ 0, else it is b\[0\]. Thus it takes O\(n\) to construct the prefixSum array. Now, sum\(i, j\) is prefixSum\[j\] - prefixSum\[i - 1\] if i ≥ 0, else it is simply prefixSum\[j\]. Thus we find sum\(i, j\) in O\(1\), meaning we can find dp\[i\]\[j\] in O\(n\). Since we depend on smaller subarrays to find the minimum time for the larger subarrays, we should find the dp\[\]\[\] values in the order of increasing subarray size. The dp\[\]\[\] values of subarrays whose sizes are 1 and 2 can be trivially found. Since there are O\(n2\) states, the overall time complexity is O\(n3\). The answer to the original question - the minimum time to combine n layers - is stored in dp\[0\]\[n - 1\].
{% endhint %}


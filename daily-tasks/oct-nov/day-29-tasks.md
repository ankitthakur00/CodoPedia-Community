---
description: 'Date : 30 November 2020'
---

# Day 29 : Tasks

## Aptitude 

A boat covers 6 km upstream and returns back to the starting point in 2 hours. If the flow of the stream is 4 km/hr, what is the speed of the boat in still water? 

* 6 km/hr
* 7.3 km/hr
* 8 km/hr
* 5 km/hr

{% hint style="success" %}
**Ans :** 8 km/hr

Let the speed of the boat in still water = b km/hr.

6/\(b-4\) +6/\(b+4\) = 2, or

6\(b+4\) + 6\(b-4\) = 2\(b^2–16\), or

6b+24 + 6b-24 = 2b^2–32, or

2b^2–12b-32 = 0, or

b^2–6b-16 = 0

\(b-8\)\(b+2\) = 0, or

b = 8 kmph or -2 kmph \(not acceptable\)

So the speed of the boat in still water is 8 kmph.
{% endhint %}

## Technical MCQ

An Array of structures is stored in: 

* Adjacent memory location
* Random memory location
* Heap
* Stack

{% hint style="success" %}

{% endhint %}

## Coding Question

One day Neelu visited a magical place. There she got a die and a magic sequence S of length n. After inspecting the magic sequence, she decided to generate a sequence A so she rolled the die n times and wrote the numbers she got on die. She found that some of the characters were missing from the magic sequence. The magic sequence contained only Ls and Rs. The missing characters in the magic sequence were replaced with question mark\(?\) symbols.

Neelu decided to use sequence A and magic sequence S to start her journey from her home. She moves A\[i\] units left if S\[i\] is L or A\[i\] units right if S\[i\] is R. She wants to go as far as possible from her home.

Your task is to help her replace those? s with L or R such that it maximizes the distance between the endpoint and her home.

S contains only 'L', 'R' or '?'.

**`Input:`** 

```text
0 2 3 3 2 5 L?R 2 1 2 RL
```

**`Output:`** 

```text
0 4 1
```

**`Explanation:`**In the first test case, the second character of the magic sequence is '?'. If we replace it with 'L', she moves 5 units left then 5 units right hence she is at her home at the end of her journey. If we replace it with 'R' then she moves 3 units left and then 7 units right hence her distance from her home is 4 at the end of her journey. Replacing '?' with 'R' gives the maximum distance. In the second test case, she moves 1 unit right and then 2 units left hence she is at 1 unit distance from her home at the end.

### Solution:

```cpp
#include <bits/stdc++.h>
using namespace std;
int A[200007];
int main() {
  	ios::sync_with_stdio(0); cin.tie(NULL); cout.tie(NULL);
	int t; cin>>t;
    while(t--){
    	int n; cin>>n;
    	for(int i=0;i<n;i++)
    		cin>>A[i];
    	string S; cin>>S;
    	int left = 0, right = 0, unknown = 0;
    	for(int i=0;i<n;i++){
    		if(S[i]=='L')
    			left += A[i];
    		else if(S[i] == 'R')
    			right += A[i];
    		else
    			unknown += A[i];
    	}
    	int ans = abs(left - right) + unknown;
    	cout<<ans<<'\n';
    }
  	return 0;
}
```


---
description: 12-11-2020
---

# Day 14 : Tasks

## Aptitude

Given 5 boys and 5 girls sitting in a row randomly. Find the probability that all the 5 girls sit together.

1. 1/462
2. 1/42
3. 1/21
4. 1/252

{% hint style="success" %}
Answer: 1/42

B = 5 G = 5

x = 10

\(6!×5!\)/10!=\(6!×5×4×3×2×1\)/\(10×9×8×7×6\)=1/42
{% endhint %}



## Technical

Which Scheduler effects the degree of multi-programming?

1. Long Term Scheduler
2. Short Term Scheduler
3. Medium Term Scheduler
4. All of the above

{% hint style="success" %}
Answer: Long Term Scheduler
{% endhint %}

## Coding Question

You are given two string A and B that are made of lowercase English alphabets. Find the number of different pairs \(\(i,j\),\(k,l\)\) such that the substrings A\[i….j\] and B\[k….l\] are equal and the value of j-i+1 is minimum.

Input : abdc bd

Output: 2

Explanation: pairs are \(\(1,1\), \(0,0\)\) and \(\(2,2\),\(1,1\)\)

## Solution:

```cpp
int solve(string s1 , string s2)
{
	int n1 = s1.size();
	int n2 = s2.size();
	   int freq1[26] = { 0 }; 
    int freq2[26] = { 0 }; 
    int i, count = 0; 
 
    for (i = 0; i < n1; i++) 
        freq1[s1[i] - 'a']++; 
 
    for (i = 0; i < n2; i++) 
        freq2[s2[i] - 'a']++; 
 
    for (i = 0; i < 26; i++) 
        count +=(freq1[i]* freq2[i]); 
  
    return count; 
}
```


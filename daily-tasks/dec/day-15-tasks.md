---
description: 'Date : December 15, 2020'
---

# Day 15 : Tasks

## Aptitude

A sum of money is divided among A, B, C so that for each rupee A gets, B gets 75 paise and C gets 45 paise. If C's share is Rs. 81, the sum is   
A\) Rs. 326   
B\) Rs. 639   
C\) Rs. 396   
D\) Rs. 369

{% hint style="success" %}
Answer - 396\(c\)   
A : B : C =100 : 75 : 45 = 20 : 15 : 9   
If C's share is Rs. 9, then the sum is Rs. 44.   
If C's share is Rs.81, then Sum = Rs \(\(44/9\)×81\) = Rs. 396
{% endhint %}

## Technical

Consider a virtual memory system with FIFO page replacement policy.   
For an arbitrary page access pattern, increasing the number of page frames in main memory will   
a\) Always decrease the number of page faults   
b\) Always increase the number of page faults   
c\) Some times increase the number of page faults   
d\) Never affect the number of page faults

{% hint style="success" %}
Answer: \(c\)   
Explanation: Incrementing the number of page frames doesn’t always decrease the page faults \(Belady’s Anomaly\)
{% endhint %}

## Coding

Given a string **S** and a string **T**, check if **S** is a subsequence of **T**.  
A subsequence of a string is a new string that is formed from the original string by deleting some \(can be none\) of the characters without disturbing the relative positions of the remaining characters. \(ie, "ace" is a subsequence of "abcde" while "aec" is not\).

Follow up: If there are lots of incoming **S**, say **S1, S2, ... , Sk** where **k &gt;= 1B**, and you want to check one by one to see if **T** has its subsequence. In this scenario, how would you change your code?

**Example 1:**  
_Input:_   
s = "abc", t = "ahbgdc"   
_Output:_   
true   
**Example 2:**  
_Input:_   
s = "axc", t = "ahbgdc"   
_Output:_   
false

#### Solution

```cpp
bool isSubsequence(string t, string s) {
        if(t.size()==0)
            return true;
        int j=0;
        int k=t.size();
        for(int i=0;i<s.size();i++)
        {
            if(s[i]==t[j])
                j++;
            if(j==k)
                return true;
        }
        return false;
    }
```


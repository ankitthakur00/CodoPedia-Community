---
description: 'Date : January 7 ,2021'
---

# Day 7 : Taks

## Aptitude

A candidate got 5650 votes in an election and won by this opponent by a margin of 3000 votes. if there only two candidates, find the percentage of votes obtained by the defeated candidate.  
1. 30.5  
2. 31.93  
3. 32.65  
4. 30.72  


{% hint style="success" %}
Answer = 31.93%  
candidate got =5650votes  
losing candidate =5650−3000=2650  
%  obtained by loosing candidate = \(2650/\(5650+2650 \)\) \* 100  
= 31.93 %
{% endhint %}

## Technical

If we preempt a resource from a process, the process cannot continue with its normal execution and it must be _\_\__   
a\) aborted   
b\) rolled back   
c\) terminated   
d\) queued

{% hint style="success" %}
Answer: b
{% endhint %}

## Coding

There is a strange printer with the following two special requirements:  
The printer can only print a sequence of the same character each time.  
At each turn, the printer can print new characters starting from and ending at any places, and will cover the original existing characters.  
Given a string consists of lower English letters only, your job is to count the minimum number of turns the printer needed in order to print it.  
**Example 1:**  
_Input:_   
"aaabbb"   
_Output:_   
2   
_Explanation:_   
Print "aaa" first and then print "bbb".**Example 2:**  
_Input:_   
"aba"   
_Output:_   
2   
_Explanation:_   
Print "aaa" first and then print "b" from the second place of the string, which will cover the existing character 'a'.  
**Hint: Length of the given string will not exceed 100.**

```cpp
int strangePrinter(string s) {
        if (s.empty()) return 0;
        vector<vector<int>> m(s.length(), vector<int>(s.length() + 1,INT_MAX));
        for (int i = 0; i < s.length(); ++i) m[i][1] = 1;

        for (int len = 2; len <= s.length(); ++len) {
            for (int i = 0; i + len <= s.length(); ++i) {
                int val = (s[i] == s[i + len - 1]);
                for (int j = i + len - 1; j > i; --j) {
                    m[i][len] = min(m[i][len], m[i][j - i] + m[j][i + len - j] - val);
                }
            }
        }
        return m[0][s.length()];
    }
```


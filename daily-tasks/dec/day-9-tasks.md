---
description: 'Date : December 9, 2020'
---

# Day 9 : Tasks

## Aptitude

In how many different ways can the letters of the word 'OPTICAL' be arranged so that the vowels always come together?  
1. 120  
2. 720  
3. 4320  
4. 2160  
5. None

{% hint style="success" %}
The word 'OPTICAL' contains 7 different letters.  
 When the vowels OIA are always together, they can be supposed to form one letter.   
Then, we have to arrange the letters PTCL \(OIA\). Now, 5 letters can be arranged in 5! = 120 ways.   
The vowels \(OIA\) can be arranged among themselves in 3! = 6 ways.  
 ∴ Required number of ways = \(120 x 6\) = 720.
{% endhint %}

## Technical

Which of the following is not a DDL command?   
a\) UPDATE   
b\) TRUNCATE   
c\) ALTER   
d\) None of the Mentioned

{% hint style="success" %}
Answer: a   
Explanation:   
Data definition language \(DDL\) commands enable you to perform the following tasks:  
Create, alter, and drop schema objects.
{% endhint %}

## Coding

Given a string A containing just the characters ’\(‘ and ’\)’.

Find the length of the longest valid \(well-formed\) parentheses substring.

Input 1:   
A = "\(\(\)"   
Output 1: 2   
Explanation 1:   
The longest valid parentheses substring is "\(\)", which has length = 2.

Input 2:   
A = "\)\(\)\(\)\)"   
Output 2:   
4  
Explanation 2:   
The longest valid parentheses substring is "\(\)\(\)", which has length = 4.

#### Explanation

{% hint style="success" %}
Let's construct longest\[i\] where longest\[i\] denotes the longest set of parenthesis ending at index i.  
If s\[i\] is ‘\(‘, set longest\[i\] to 0,    
because any string end with ‘\(‘ cannot be a valid one.   
Else if s\[i\] is ‘\)’   
If s\[i-1\] is ‘\(‘,   longest\[i\] = longest\[i-2\] + 2   
Else if s\[i-1\] is ‘\)’ and  s\[i-longest\[i-1\]-1\] == ‘\(‘, longest\[i\] = longest\[i-1\] + 2 + longest\[i-longest\[i-1\]-2\]
{% endhint %}

#### Solution

```cpp
int Solution::longestValidParentheses(string A) {
    stack<int> s;
    int n = A.length(), i = 0;
    int res = 0;
    
    while(i < n){
        if(s.empty() || A[i] == '(' || (A[s.top()] == ')'))
            s.push(i);
        else{
            s.pop();
            int ans = s.empty() ? i + 1 : i - s.top();
            res = max(res, ans);
        }
        i++;
    }
    return res;
}
```


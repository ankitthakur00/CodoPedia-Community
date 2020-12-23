---
description: 23 December 2020
---

# Day 23 : Tasks

## Technical

The circular wait condition can be prevented by _\_\_\_\_\_\_\_._

1.  defining a linear ordering of resource types
2. using threads
3. using pipes
4. all of the mentioned

{% hint style="success" %}
**Answer:** defining a linear ordering of resource types
{% endhint %}

## Coding Question

Find the lexicographically smallest sub sequence of exactly k length in a given string.

```text
Input:
2
bbxabfc
3
iftygoprthxzad
6

Output:
abc
fghxad
```

## Solution:

```cpp
string lexico_smallest_sub_seq(string& s, int k) {
     string p="";
 
    deque<int>q;
    for(int i=0;i<s.size();i++)
    {
        while(!q.empty() && s[q.back()]>s[i] && q.size()+s.size()-i-1>=k)
        q.pop_back();
        q.push_back(i);
    }
  
    while(!q.empty() && p.size()<k)
    {
        p+=s[q.front()];
        q.pop_front();
    }
    return p;
}
```


---
description: 12th January 2021
---

# Day 12 : Tasks

## Technical

A state is safe, if _\_\__

1. the system does not crash due to deadlock occurrence 
2. the system can allocate resources to each process in some order and still avoid a deadlock 
3. the state keeps the system protected and safe 
4. all of the mentioned

{% hint style="success" %}
**Answer:** the system can allocate resources to each process in some order and still avoid a deadlock 
{% endhint %}

## Coding Question

Given an array equations of strings that represent relationships between variables, each string equations\[i\] has length 4 and takes one of two different forms: "a==b" or "a!=b". Here, a and b are lowercase letters \(not necessarily different\) that represent one-letter variable names.

Return true if and only if it is possible to assign integers to variable names so as to satisfy all the given equations.

```text
Example 1:

Input: ["a==b","b!=a"]
Output: false
Explanation: If we assign say, a = 1 and b = 1, then the first equation is satisfied, but not the second.  There is no way to assign the variables to satisfy both equations.
Example 2:

Input: ["b==a","a==b"]
Output: true
Explanation: We could assign a = 1 and b = 1 to satisfy both equations.
Example 3:

Input: ["a==b","b==c","a==c"]
Output: true
Example 4:

Input: ["a==b","b!=c","c==a"]
Output: false
Example 5:

Input: ["c==c","b==d","x!=z"]
Output: true
```

_First, going through equality equations and use the union operation to join the variables in one set._

_Second, going through inequality equations and verify that the variables are not in the same set using the find operation._

_In the end, there are two sets \[a, c, d, f\] and \[b, e, g\]._

## Solution:

```cpp
int uf_find(vector<int> &uf, int i) {
  return uf[i] == -1 || uf[i] == i ? i : uf_find(uf, uf[i]);
}
bool equationsPossible(vector<string>& equations) {
  vector<int> uf('z' + 1, -1);
  for (auto s : equations)
    if (s[1] == '=') uf[uf_find(uf, s[0])] = uf_find(uf, s[3]);
  for (auto s : equations)
    if (s[1] == '!' && uf_find(uf, s[0]) == uf_find(uf, s[3])) return false;
  return true;
}
```


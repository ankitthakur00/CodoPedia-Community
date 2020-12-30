---
description: 30th December 2020
---

# Day 30 : Tasks

## Aptitude 

## A and B are two alloys of gold and copper prepared by mixing metals in the proportions 7 : 2 and 7 : 11 respectively. If equal quantities of the alloys are melted to form a third alloy C, proportion of gold and copper in C will be

1. 5:7
2. 5:9
3. 7:5
4. 9:5

{% hint style="success" %}
**Answer:** 7 : 5

Explanation: Gold in C = \(7/9+7/18\)

= 21/18=76

Copper in C = \(2/9+11/18\)

= 15/18=56

Gold : Copper = 7/6:5/6

= 7 : 5
{% endhint %}

## Technical

Which of these is not a correct statement?

1. Every class containing abstract method must be declared abstract
2.  Abstract class defines only the structure of the class not its implementation
3. Abstract class can be initiated by new operator
4. Abstract class can be inherited

{% hint style="success" %}
**Answer:** Abstract class can be initiated by new operator

Explanation: Abstract class cannot be directly initiated with new operator, Since abstract class does not contain any definition of implementation it is not possible to create an abstract object.
{% endhint %}

## Coding

Given an integer matrix, find the length of the longest increasing path.

From each cell, you can either move to four directions: left, right, up or down. You may NOT move diagonally or move outside of the boundary \(i.e. wrap-around is not allowed\).

```text
Example 1:

Input: nums = [ [9,9,4], [6,6,8], [2,1,1] ]
 Output: 4 
Explanation: The longest increasing path is [1, 2, 6, 9]. 
```

```text
Example 2:

Input: nums = [ [3,4,5], [3,2,6], [2,2,1] ]
 Output: 4 
Explanation: The longest increasing path is [3, 4, 5, 6]. Moving diagonally is not allowed.
```

## Solution:

```cpp
int dfs(vector<vector<int>>& m, int i, int j, int v, vector<vector<int>>& len)
{
  if (i < 0 || j < 0 || i == m.size() || j == m[0].size() || m[i][j] <= v) return 0;
  return len[i][j] > 0 ? len[i][j] : len[i][j] = 1 + max(
    max(dfs(m, i - 1, j, m[i][j], len), dfs(m, i + 1, j, m[i][j], len)),
    max(dfs(m, i, j - 1, m[i][j], len), dfs(m, i, j + 1, m[i][j], len)));
}

int longestIncreasingPath(vector<vector<int>>& m, int res = 0) 
{
  vector<vector<int>> len(m.size(), vector<int>(m.size() == 0 ? 0 : m[0].size()));
  for (auto i = 0; i < m.size(); ++i)
    for (auto j = 0; j < m[0].size(); ++j) res = max(res, dfs(m, i, j, m[i][j] - 1, len));
  return res;
}
```


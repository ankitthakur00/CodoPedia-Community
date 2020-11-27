---
description: 'Date : 22 November 2020'
---

# Day 21 : Tasks

## Aptitude

Find the common difference of an AP. whose first term is 100 and the sum of whose first six-term is five times the sum of the next six terms.  
10   
-10   
5  
-5

{% hint style="success" %}
Answer: -10  
  
Here a=100

Let difference is d. ⇒a1 +a2 +a3+a4 +a5+a6=5\(a7 +a8+a9+a10+a11+a12 \)

⇒6\( a1 +a6\)/2=5×6\( a7 +a12 \)/2

⇒a1+a6=5\(a7 +a12 \)

⇒a+a+5d=5\(a+6d+a+11d\)

⇒2a+5d=10a+85d

⇒80d=−8a

⇒d= -a/10 ​  
⇒ -100/10 ​  
⇒−10
{% endhint %}

## Technical

Which algorithm is used to check the negative cycle in the graph?  
1. Prim's Algorithm  
2. Kruskal Algorithm  
3. Bellman Ford Algorithm  
4. Floyd Warshall Algorithm

{% hint style="success" %}
Bellman-Ford Algorithm is used to check negative cycles.  
Negative cycle is a cycle whose sum of edges result in negative value.
{% endhint %}

## Coding question

Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.   
Example:   
Input: "aab"   
Output: \[ \["aa","b"\], \["a","a","b"\] \]

### Solution

```cpp
class Solution {
public:
    vector<vector<string>> partition(string s) {
        int len = s.length();
        vector<vector<bool>> dp (len, vector <bool> (len, false));
        vector<vector<string>> result;
        vector<string> currentList;
        dfs(result, s, 0, currentList, dp);
        return result;
    }

    void dfs(vector<vector<string>> &result, string &s, int start, vector<string> &currentList, vector<vector<bool>> &dp) {
        if (start >= s.length()) result.push_back(currentList);
        for (int end = start; end < s.length(); end++) {
            if (s[start] == s[end] && (end - start <= 2 || dp[start + 1][end - 1])) {
                dp[start][end] = true;
                currentList.push_back(s.substr(start, end - start + 1));
                dfs(result, s, end + 1, currentList, dp);
                currentList.pop_back();
            }
        }
    }
};
```

### Explanation

```text
A given string s starting at index start and ending at index end is a palindrome if following conditions are satisfied :
1.	The characters at start and end indexes are equal.
2.	The substring starting at index start+1 and ending at index end−1 is a palindrome.
 
Let N be the length of the string. 
To determine if a substring starting at index start and ending at end is a palindrome or not, 
we use a 2 Dimensional array dp of size  N⋅N where,
dp[start][end]=true , if the substring beginning at index  start and ending at index end is a palindrome.
Otherwise dp[start][end] ==false.
Also, we must update the dp array, if we find that the current string is a palindrome
```


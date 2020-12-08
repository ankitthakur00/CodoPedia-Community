---
description: 'Date : December 8, 2020'
---

# Day 8 : Tasks

## Aptitude

A boy walking at a speed of 10 km/hr reaches his school 15 minutes late. Next time he increases his speed by 2 km/hr, but still, he is late by 5 minutes. Find the distance of his school from his house.  
1. 10 km  
2. 15 km  
3. 20 km  
4. 25 km

{% hint style="success" %}
Answer: 10km  
  
Let the distance of his school from the house be x.

diffence in time = \(15-5\) mins = 1/6 hour.

speed during next journey = 10+2 = 12km/hr .

ATQ, \(x/10\) - \(x/12\) = \(1/6\) on solving this, x = 10 .
{% endhint %}

## Technical

When does page fault occur?

a\) The page is present in memory.   
b\) The deadlock occurs.   
c\) The page does not present in memory.  
d\) The buffering occurs

{% hint style="success" %}
Answer: \(c\) The page does not present in memory.

Explanation: Page faults occur when a process tries to access a block page of the memory and that page is not stored in RAM \(Read-only memory\) or memory
{% endhint %}

## **Coding Question \(Asked in Zeta recently\)**

#### Problem Statment

There are N boxes placed in a row and M diamonds are distributed in these boxes such that each box contains at least one diamond in it. Each diamond has color Ci and value Vi placed into box Bi. Now your task is to take exactly one diamond from each box such that the total value of diamonds taken is maximum and diamonds taken from two consecutive boxes are of different colors. Print -1 if this condition can't be satisfied.

#### Input Format

First-line contains integers N and M.   
Next M lines contain values of Bi , Ci and Vi respectively.

#### Sample Test Cases :

Input :   
4 4  
2 1 5   
4 3 4   
1 3 7   
3 2 3  
Output :   
19  
  
Input :   
3 3   
1 1 9   
2 3 11   
3 3 5  
Output :  
 -1

### Explanation

{% hint style="success" %}
Think of a recursive solution and identify states.  
Memoize the recursive solution to optimize it.
{% endhint %}

### Solution

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long
#define N 100001
#define f first
#define s second

vector<pair<ll, ll>> box[N];
ll dp[N][8];
ll n, m;

ll rec(ll curr, ll col)
{
	if (curr > n) return 0;

	if (dp[curr][col] != -1)
		return dp[curr][col];

	ll ans = -1e15;
	for (int i = 0; i < box[curr].size(); i++)
	{
		if (box[curr][i].f != col) {
			ans = max(ans, box[curr][i].s + rec(curr + 1, box[curr][i].f));
		}
	}
	return dp[curr][col] = ans;
}

int main()
{
		memset(dp, -1, sizeof(dp));
		for (int i = 0; i < N; i++)
			box[i].clear();
		cin >> n >> m;
		for (int i = 0; i < m; i++)
		{
			ll b, c, val;
			cin >> b >> c >> val;
			box[b].push_back({c, val});
		}

		ll ans = 0;
		ans = rec(1, -1);
		if (ans < -1e9) ans = -1;

		cout << ans << endl;
	
	return 0;
}
```

  
  
  



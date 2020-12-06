---
description: 06-12-2020
---

# Day 6: Tasks

## Aptitude

Find the missing term: 2, 3, 5, 7, 11, ?, 17

A. 12

B. 13

C. 14

D. 15

{% hint style="success" %}
**Ans** : 13  
  
Clearly, the given series consists of prime numbers starting from 2. So, the missing term is the prime number after 11, which is 13.
{% endhint %}

## Technical MCQ

 A binary tree has 20 nodes. Then how many null branches have the tree?

* 0
* 20
* 21
* 40

{% hint style="success" %}
Ans : 21  
If the tree has 3 nodes then it has 4 null branches.ie 3+1. If the tree has 5 nodes then it has 6 null branches.ie 5+1.  
 In general a binary tree with n nodes has exactly n+1 null nodes. So 20 nodes has 21 null branches.
{% endhint %}

## 

## Coding Question

There are a row of N houses, each house can be painted with one of the three colors: red, blue or green.

The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color.

The cost of painting each house with a certain color is represented by a N x 3 cost matrix A.

For example, A\[0\]\[0\] is the cost of painting house 0 with color red; A\[1\]\[2\] is the cost of painting house 1 with color green, and so on.

Find the minimum total cost to paint all houses.

```cpp
Input :
A = [ [1, 2, 3] [10, 11, 12] ]
Output : 12
```

Example Explanation Explanation 1:

Paint house 1 with red and house 2 with green i.e A\[0\]\[0\] + A\[1\]\[1\] = 1 + 11 = 12

### **Solution :**

{% hint style="success" %}
Let:

1. dp\[i\]\[0\] represent the minimum total cost to paint the houses till i where house i is colored in red.
2. dp\[i\]\[1\] represent the minimum total cost to paint the houses till i where house i is colored in green.
3. dp\[i\]\[2\] represent the minimum total cost to paint the houses till i where house i is colored in blue.

So if you paint house ‘i’ with red then you can paint house ‘i-1’ only in blue or green.  
So dp\[i\]\[0\] = A\[i\]\[0\] + min\(dp\[i-1\]\[1\],dp\[i-1\]\[2\]\)  
Similarly:  
dp\[i\]\[1\] = A\[i\]\[1\] + min\(dp\[i-1\]\[0\], dp\[i-1\]\[2\]\)  
dp\[i\]\[2\] = A\[i\]\[2\] + min\(dp\[i-1\]\[0\], dp\[i-1\]\[1\]\)

At last output the minimum of \(dp\[n-1\]\[0\],dp\[n-1\]\[1\],dp\[n-2\]\[2\)

**Time Complexity:**O\(N\).  
**Space Complexity:**O\(N\).
{% endhint %}

```cpp
int Solution::solve(vector<vector<int> > &A) {
    int n=A.size();
    int dp[n+1][3];
    int i,j;
    for(i=0;i<=2;i++)
    dp[0][i]=0;
    for(i=1;i<=n;i++)
    {
        dp[i][0]=A[i-1][0]+min(dp[i-1][1],dp[i-1][2]);
        dp[i][1]=A[i-1][1]+min(dp[i-1][0],dp[i-1][2]);
        dp[i][2]=A[i-1][2]+min(dp[i-1][0],dp[i-1][1]);
    }
    
    return min(dp[n][0],min(dp[n][1],dp[n][2]));
}
```


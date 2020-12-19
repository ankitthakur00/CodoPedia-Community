---
description: 19 December 2020
---

# Day 19 : Tasks

## Aptitude

## If a man travels @ 10 km/hr from A  to B and again @ 15 km/hr from B to A Find the average speed of man for complete journey

1. 8
2. 10
3. 12
4. 14

{% hint style="success" %}
**Answer: 12**

Avg. speed = **\(**2×10×15\)/\(10+15\)=\(2×10×15​\)/25=12 km/hr 
{% endhint %}

## Technical

The command used to delete a particular column in a relation is _\_\_\_\_\_\_\_._

1. Update Table
2. Truncate Column
3. Alter, Drop
4. Delete Column

{% hint style="success" %}
Answer : ALTER , DROP
{% endhint %}

## Coding Question

There are N Algorithm Experts and N-1 Software Developers. You as Project manager will exclude an Algorithm Expert and form N-1 teams each consist of a software developer and an algorithm expert such that the efficiency of the whole project is maximised, but the problem is you can't jumble the ordering as the employees won't be happy.

There is an array algoExperts\[\] which denotes the skill of ith algorithm expert and an array Developers\[\] which denotes the skill of ith software developer.

Efficency of a team is given by the product of the skill of software developer and the algorithm expert, and total efficiency is the sum of the efficiencies of N-1 teams.

```text
Example: 
Input:
2
5
4 1 5 2 9
1 2 1 1
2
4 1
1
Output:
25
4
```

```text
Explanation:
Testcase 1: 2nd Algorithm Expert is excluded and the maximum efficiency will be 4*1 + 5*2 + 2*1 + 9*1 = 25.
Testcase 2: 2nd Algorithm Expert is excluded and the maximum efficiency will be 4*1 = 4.
```

## Solution:

```cpp
long long int project(long long int a[], long long int d[], int n)
{
   
    long long int left=0,right=0,f=0;
    for(int i=0;i<n-1;i++)
     left+=a[i]*d[i];
    long long int sum=left;
    for(int i=n-1;i>=1;i--)
    {
        left-=(a[i-1]*d[i-1]);
        right+=(a[i]*d[i-1]);
        sum=max(sum,left+right);
    }
    return sum;
    
}
```


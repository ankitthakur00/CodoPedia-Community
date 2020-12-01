---
description: 'Date: 5 November 2020'
---

# Day 7: Tasks

## Aptitude

A Cow is tethered in the middle of the field with a 14m long rope. if the cow grazes 100sq.ft per day,  then approximately what time will be taken by the cow to graze the whole field? 

{% hint style="success" %}
**Ans:** 6 Days

Area of field =πr^2 ​  
Area=22/7 ×\(14×14\)=616ft

No,of days required = 616/100=6.16≃6 days
{% endhint %}

## Technical MCQ

Sort the given elements in ascending order using selection sort: 10 3 4 1 9 12 18 What will be child node\(s\) of 12 when the max heap is constructed from the elements of the 3rd pass of the sorting algorithm

1. 9
2. 4 and 10
3. 1 and 3
4. 12

{% hint style="success" %}
**Ans:** 4 and 10

3rd Pass of selection sort will be:

 1 3 4 10 9 12 18 

There will be 2 ways to create a heap

 a\) We will insert elements from the start in the heap 

b\)We will insert elements from the end in the heap

Child nodes of 12 in case 1 are: 3 and 10 Child nodes of 12 in case 2 are: 4 and 10

4 and 10 matches one of the answers given.

**Note:** In online rounds of big companies like GS they mostly doesn't specify things so we have to take all possibilities and check whether we are getting answers from the given options or not. That's why here we have taken 2 possibilities.
{% endhint %}

## Coding Question

You are given an array of integers. You have to start from the first index and reach the end. The only steps you can take are +3 or -1. The cost of a path is equal to the sum of all integers in the path. Find the cost of the lowest cost path. If no path is possible, print -1.

**Input:**

```text
8
3 1 2 5 10 100 200 20
```

**Output :** 

```text
41
```

`Most optimised path is 3 -> 5 -> 2 -> 1 -> 10 -> 20. Sum of elements in this path is 41.`

**`Try to Solve in o(n)`**

{% hint style="info" %}
**Explanation :** If we take +3 step from ith index then cost to reach \(i+3\)th index will be minimum of \(minimum cost to reach ith index + cost at \(i+3\)th index i.e a\[i+3\] , previous minimum cost to reach \(i+3\)th index\)

From \(i+3\)th index we can move to \(i+2\)th index so cost to reach \(i+2\)th index will be minimum of \(minimum cost to reach \(i+3\)th index + cost at \(i+2\)th index i.e a\[i+2\] , previous minimum cost to reach \(i+2\)th index\)

Similarly, from \(i+2\)th index we can go back to \(i+1\)th index

We will not go back to ith index from \(i+1\)th index because that will not be the minimum to reach ith index
{% endhint %}

**Solution:**

```cpp
int min_cost(int* a ,int n)
{
    vector<int>v(n,INT_MAX);
    v[0]=a[0];
    for(int i=0;i<n-3;i++)
    {
        v[i+3]=min(v[i]+a[i+3],v[i+3]);
        v[i+2]=min(v[i+3]+a[i+2],v[i+2]);
        v[i+1]=min(v[i+1],v[i+2]+a[i+1]);
    }
    return v[n-1];
}
```


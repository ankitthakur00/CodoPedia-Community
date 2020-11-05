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


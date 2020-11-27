---
description: 'Date: 1 November 2020'
---

# Day 3: Tasks

## Aptitude

Dimpy scored the following marks in 5 different subjects 86, 95, 94, 88, 80. If she wishes to earn a 90 avg. What must she score on her next subject?

1. 90 
2. 97 
3. 96 
4. 95
5.  89

{% hint style="success" %}
97  
  
Let marks in next subject be x ,  
\(86+95+94+88+80+x\)/6 = 90  
solve for x
{% endhint %}

## Technical MCQ

What is it called when an object has its own lifecycle and there is no owner?

1. aggregation 

2. composition 

3. Association 

4. Encapsulation

{% hint style="success" %}
Association

**Association** is a semantically weak relationship \(a semantic dependency\) between otherwise unrelated objects. An **association** is a “using” relationship between two or more objects in which the objects have their own lifetime and there is no owner.
{% endhint %}

## Coding Question

A sub-sequence of an array is formed by removing zero or more elements from an array without changing the order of the remaining elements. In a valid sub-sequence, each pair of adjacent elements of the subsequence has bit-wise XOR equal to k.

Note that any sub-sequence of length 1 is valid regardless of the value of k. because there is no pair of adjacent elements in such a sub-sequence.

Given an array of integers and integer k, determine the length of the longest valid sub-sequence in the array.

**Try to Solve in o\(n\)**



```text
Example: N= 5
arr= [2 1 3 5 2]
 k= 2
Output : 2 (longest sub-sequence with xor of all adjacent equal to k is {1,3})
```

### Solution:

```cpp
 int maxSubsequenceLength(int n,int v[],int k)
{
    unordered_map<int,int>m;      // To store longest subsequence till  particular element
    int c=1;                                           // store length of longest subsequence   
    for(int i=n-1;i>=0;i--)                // traverse array from end to start
    {
            if(m.count(v[i]^k)) 	// check if xor of v[i] and k present in map if yes then 
            {
                if(m[v[i]^k]+1>c)   // check length till (v[i]^k) value +1 is greater than our longest subsequence length  if yes then
               {
                    c=m[v[i]^k]+1;   // replace our longest subsequence variable 
                }
                   m[v[i]]=m[v[i]^k]+1;   // store length of longest subsequence till v[i]
            }
            else
        m[v[i]]=1;
    }
    return c;
}
```

 




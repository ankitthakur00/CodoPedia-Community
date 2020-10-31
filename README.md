---
description: 'Date : 30 October 2020'
---

# Day 1: Tasks

## Aptitude

Munna Bhaiya and Guddu Bhaiya can complete work in 48 days. Munna Bhaiya alone can complete in 64 days. Munna Bhaiya and Guddu Bhaiya worked together for 30 days. In how many days Guddu Bhaiya alone can complete the remaining work.

1. 64
2. 24
3. 72
4. 36

{% hint style="info" %}
Ans : 72 Days
{% endhint %}

## Technical MCQ

In an operating system, which of the following is CPU bound process. 1. Interactive shell 2. File Transfer 3. Sorting a million entry array 4. None of the above

1. Interactive shell 
2. File Transfer 
3. Sorting a million entry array  
4. None of the above$ give me super-powers

{% hint style="info" %}
 Ans:  Sorting a million entry array
{% endhint %}

## Coding Question

The i-th person has weight people\[i\], and each boat can carry a maximum weight of limit.

Each boat carries at most 2 people at the same time, provided the sum of the weight of those people is at most limit.

Return the minimum number of boats to carry every given person. \(It is guaranteed each person can be carried by a boat.\)

**Input:**

```text
[3,2,2,1]  limit=3
```

**Output:**

```text
3
```

* Try to solve in O\(nlogn\).

**Solution:**

```cpp
int numRescueBoats(vector<int>& p, int limit) {       
sort(p.begin(),p.end());
        int count=0;
        int i=0,j=p.size()-1;
        while(i<=j)
        {
            if(p[i]+p[j]<=limit)
            {
                i++;j--;
            }
            else
                j--;
            count++;
        }
        if(i==j)
            count++;
        return count;
    }
```




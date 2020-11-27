---
description: 'Date: 20 November 2020'
---

# Day 19 : Tasks

## Technical MCQ

An array was initially empty and we used a linear probing hash table of fixed size 10, and the following hash functions.

`M->7, P->0, A->5,B->6,Y->9,L->6,E->9,Q->1, W->7,S->3` 

What would be the array after inserting the following keys? 

`M,P,A,B,Y,L,E,Q,W,S` 

* P E Q A B M W S L Y
* P E Q W S A B M L Y
* Q W S A B M L Y P E
* P E A B Q W S M L Y

{% hint style="success" %}
**Ans :** P E Q W S A B M L Y
{% endhint %}

## Coding Question

Koko loves to eat bananas. There are N piles of bananas, the i-th pile has piles\[i\] bananas. The guards have gone and will come back in H hours. Koko can decide her bananas-per-hour eating speed of K. Each hour, she chooses some pile of bananas, and eats K bananas from that pile. If the pile has less than K bananas, she eats all of them instead, and won't eat any more bananas during this hour.

Koko likes to eat slowly, but still wants to finish eating all the bananas before the guards come back. Return the minimum integer K such that she can eat all the bananas within H hours.

**Input:** 

```text
piles = [30,11,23,4,20], H = 5 
```

**Output:** 

```text
30
```

`Solve in nlogn`

#### **Solution:**

```cpp
int minEatingSpeed(vector<int>& piles, int H) {
     int low=1,high=*max_element(piles.begin(),piles.end());
        while(low<high)
        {
            long long int count=0,mid=low+(high-low)/2;
            for(int i=0;i<piles.size();i++)
                count+=ceil((float)piles[i]/mid);
            if(count<=H)
                high=mid;
            else
                low=mid+1;
        }
        return low;
    }
```


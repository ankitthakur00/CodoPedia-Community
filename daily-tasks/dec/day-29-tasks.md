---
description: 'Date: 29 December 2020'
---

# Day 29: Tasks

## Aptitude

A man has 9 friends, 4 boys, and 5 girls. In how many ways can invite them, if there have to be exactly three girls in the invites?

* 320
* 160
* 80
* 200

{% hint style="success" %}
**Ans:**160

`He can select three girls in 5C3​ ways = 10 ways  
He can select boys in  [4C0​+4C1​+4C2​+4C3​+4C4​] ways = 16 ways  
Total number of ways =10×16 =160`
{% endhint %}



## Technical MCQ

Which of the following is correct? 

a\) Base class pointer object cannot point to a derived class object 

b\) Derived class pointer object cannot point to a base class object 

c\) A derived class cannot have pointer objects 

d\) A base class cannot have pointer objects

{% hint style="success" %}
**Ans:** b 

**`Explanation:`**`C++ does not allow a derived class pointer to point a base class pointer whereas a Base class can point to a derived class object. Both base class and derived class can have pointer objects.`
{% endhint %}

## Coding

Given a non-negative integer n, count all numbers with unique digits, x, 

where 0 ≤ x &lt; 10n.

**Example:**

```cpp
Input: 
2 

Output: 
91
```

**`Explanation:`** `The answer should be the total numbers in the range of 0 ≤ x < 100, excluding 11,22,33,44,55,66,77,88,99`

### Solution:

```cpp
int countNumbersWithUniqueDigits(int n) {
        if(n==0)
            return 1;
        int p=9,sum=9;
        n--;
        int i=9;
        while(n--)
        {
            p=p*i;
           sum+=p;
            i--;
        }
        return sum+1;
    }
```


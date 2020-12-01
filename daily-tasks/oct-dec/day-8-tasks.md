---
description: 'Date: 6 November 2020'
---

# Day 8 : Tasks

## Aptitude

Cash difference between the selling prices of an article at a profit of 4% and 6% is Rs 3. the ratio of two selling price is?

1. 51:52
2. 51:53
3. 52:55
4. 52:53

{% hint style="success" %}
**Ans:** 52:53

Let cost price \(CP\) of the article be X rs.

For 4% profit, SP=CP+4% of CP=1.04X

For 6% profit, SP=CP+6% of CP=1.06X

It is given that cash differences between selling price is Rs 3.

⇒1.06X−1.04X=3

⇒0.02X=3

∴ X=150

i.e. Selling price of first article =1.04X=1.04×150=156 Rs

and Selling price of second article =1.06X=1.06×150=159 Rs

∴  Ratio of selling prices = 159/156 ​ =52:53
{% endhint %}



## Technical MCQ

which of the following statements about dynamic array is true? 

1. Dynamic Arrays are allocated at the runtime.
2. Array Size can be changed any number of times.
3.  Both the array element values and element memory can be deleted.
4. Memory can be utilized efficiently

**Options**

1. 1 and 3
2. 2,3, and 4
3. All of the above
4. None of these

{% hint style="success" %}
**Ans:**3. All of the above
{% endhint %}

## Coding Question

Ted is a pro coder, but today he is very busy doing college assignments. He needs your help to complete a task. The task is as follow :

Given two positive integers A and B denoting numerator and denominator of a fraction. You need to count the length of the repeated pattern of digits in the decimal part of A/B.

```text
Input: 22 7
```

```text
Output: 6
```

**`Explanation:`** `22/7 = 3.142857142857142857.... length of repeating pattern in decimal part is 6 .`

**Solution:**

```cpp
int findRepeat(int a , int b)
{
   unordered_map<int,int>m;
   int count=0;
   int r=a%b;
   while(r!=0 && !m.count(r))
   {
       m[r]=count;
       while(r<b)
       {
         count++;
         m[r]=count;
         r=r*10;
         
       }
       r=r%b;
   }
   if(r==0) return 0;
   return count-m[r]+1;
}
```


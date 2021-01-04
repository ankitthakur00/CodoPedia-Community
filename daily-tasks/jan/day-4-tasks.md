---
description: 'Date: 4 Jan 202'
---

# Day 4: Tasks

## Aptitude

A motorboat, whose speed in 15 km/hr in still water goes 30 km downstream and comes back in a total of 4 hours 30 minutes. The speed of the stream \(in km/hr\) is:

* 4
* 5
* 6
* 10

{% hint style="success" %}
**Ans:** 5
{% endhint %}

![](../../.gitbook/assets/capture%20%285%29.png)

## Technical MCQ

Which of the following cannot be static in C?

 a\) Variables  b\) Functions   c\) Structures   d\) None of the mentioned

{% hint style="success" %}
**Ans:** d
{% endhint %}

## Coding Question

Given a positive integer n, you can apply one of the following operations:

If n is even, replace n with n / 2.

If n is odd, replace n with either n + 1 or n - 1.

Return the minimum number of operations needed for n to become 1.

**Example 1:**

```cpp
Input: 
n = 8 

Output: 
3 
```

**`Explanation:`** `8 -> 4 -> 2 -> 1`

**Example 2:**

```cpp
Input: 
n = 7 

Output: 
4 
```

**`Explanation:`** `7 -> 8 -> 4 -> 2 -> 1 or 7 -> 6 -> 3 -> 2 -> 1`

**Example 3:**

```cpp
Input: 
n = 4 

Output: 
2
```

### Solution:

Divide a number by 2 ,simply implies that right shift f that number by 1 \( num &gt;&gt;1\) eg. 9=1001 9&gt;&gt;1 = 100 

So according to this question , when we encounter even number then simply divide that number by 2 ie. num = num/2; 

let's assume after increment or decrement in num it becomes num But when we encounter odd number then we have two option either num++ or num-- , in both cases after increment or decrement , we will get a even number , But which one should i choose ? we can not divide odd number but we can determine that what we get in next step after doing changes in num to get num and divide num by 2 just using right shift operater. and it should be more beneficial to get even number than odd . eg. 9=1001 case -1 9&gt;&gt;1=100 \(4\) \(it means after right shift , we get 4 , which is even \) here , we decrease 9 \(num--\) to get 8 and divide it by 2 to get 4. case -2 if we increase 9 to get 10 then after dividing by 2 , we get 5 which is odd \(not beneficial\) conclusion - we can determine,what we will get in out next to next step just simply check 2nd bit from right if it is set then we wil get odd number\(in next to next step\) , do not decrease\(in this case increase\) otherwise decrease \* eg. 9 = 10 0 1 \(in my next to next step , we will get even number if we decease \(9-&gt;8-&gt;4\) but in 11 = 10 1 1 \(if we decrease then in our next to next step , we will get odd number\(11-&gt;10-&gt;5 \) in this case , number should be increased\)

```cpp
class Solution {
public:
int integerReplacement(int num) {
long long int count=0,n=num;
while(n>1){
if((n&1)==0){
count++;
n=n/2;
}
else{
if(n==3){
count+=2;
break;
}
else{
count++;
if((n>>1)&1)
n++;
else
n--;
}
}
}
return count;
}
}
```


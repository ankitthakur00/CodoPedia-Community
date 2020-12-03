---
description: 'Date : 3 , December 2020'
---

# Day 3 : Tasks

## Aptitude

 A producer of tea blends two varieties of tea from two tea gardens one costing Rs 18 per kg and another Rs 20 per kg in the ratio 5 : 3. If he sells the blended variety at Rs 21 per kg, then his gain percent is  
1. 12%  
2. 13%  
3. 14%  
4. 15%

{% hint style="success" %}
Answer : 12%  
Suppose he bought 5 kg and 3 kg of tea.   
Cost Price = Rs. \(5 x 18 + 3 x 20\) = Rs. 150.   
Selling price = Rs. \(8 x 21\) = Rs. 168.   
Profit = 168 - 150 = 18  
So, Profit % = \(18/150\) \* 100 = 12%
{% endhint %}

## Technical

If class A is a base class and class B and C are derived from it, then class D is derived from class B and C. To avoid multiple copies of data in class D.

1. Class D needs to be inherited as virtual
2. Class B and C need to be inherited as virtual
3. Class A should be a virtual base class
4. Class A should be a container class

{% hint style="success" %}
Answer : Option 3 \(Class A should be a virtual base class\)  
Refer, [https://www.geeksforgeeks.org/virtual-base-class-in-c/amp/](https://www.geeksforgeeks.org/virtual-base-class-in-c/amp/)
{% endhint %}

## Coding

Given a positive integer A, the task is to count the total number of set bits in the binary representation of all the numbers from 1 to A.

Return the count modulo 10^9 + 7.

**Problem Constraints**   
1 &lt;= A &lt;= 109

**Input Format**   
The First and the only argument is an integer A.

**Output Format**   
Return an integer denoting the \( Total number of set bits in the binary representation of all the numbers from 1 to A \)modulo 10^9 + 7.  
  
**Example Input**   
_Input 1:_  
A = 3   
_Input 2:_  
A = 1

**Example Output**   
_Output 1:_  
4   
_Output 2:_  
1

**Example Explanation**   
_Explanation 1:_  
DECIMAL    BINARY     SET BIT COUNT   
1                   01                1   
2                   10                1   
3                   11                2   
1 + 1 + 2 = 4   
Answer = 4 % 1000000007 = 4   
  
_Explanation 2:_  
A = 1   
DECIMAL    BINARY       SET BIT COUNT   
1                   01                 1   
  
Answer = 1 % 1000000007 = 1

### Solution

{% hint style="success" %}
If we observe bits from the rightmost side at distance i then bits get inverted after 2i position in a vertical sequence.

For example A = 5;   
0 = 0000   
1 = 0001   
2 = 0010   
3 = 0011   
4 = 0100   
5 = 0101

So, we will iterate till the number of bits in the number. And we don’t have to iterate every single number in the range from 1 to A. We will perform the following operations to get the desired result.

First of all, we will add 1 to the number in order to compensate for 0. As the binary number system starts from 0. So now A = A + 1. We will keep the track of the number of set bits encountered till now. And we will initialize it with A/2. We will keep one variable which is a power of 2, in order to keep track of the bit we are computing. We will iterate till the power of 2 becomes greater than A. We can get the number of pairs of 0s and 1s in the current bit for all the numbers by dividing A by the current power of 2. Now we have to add the bits in the set bits count. We can do this by dividing the number of pairs of 0s and 1s by 2 which will give us the number of pairs of 1s only and after that, we will multiply that with the current power of 2 to get the count of ones in the groups. Now there may be a chance that we get a number as a number of pairs, which is somewhere in the middle of the group i.e. the number of 1s are less than the current power of 2 in that particular group. So, we will find modulus and add that to the count of set bits. Time Complexity : O\(logA\)
{% endhint %}

```cpp
int Solution::solve(int A) {
    long long int k = 1;
    int mod = 1000000007;
    A++;
    //as 0 is our start in complete seq, hence A++.
    long long int count = 0;
    int temp;
    while(k < A) {
        k *= 2;
        temp = A - (A % k);
        count = (count + temp / 2) % mod;
        if((A - temp) > (k/2)) {
            temp = A - temp - k/2;
            count = (count + temp) % mod;
        }
    }
    return (int) count;
}
```


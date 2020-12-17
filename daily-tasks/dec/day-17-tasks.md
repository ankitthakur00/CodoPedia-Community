---
description: 'Date: 17 December 2020'
---

# Day 17 : Tasks

## Aptitude

A sum of money is divided among A, B, C, and D in the ratio of **`3 : 4 : 9 : 10`** respectively. If the share of C is Rs.2,580 more than the share of B, then what is the total amount of money of A and D together? 

* 5676
* 6192
* 6708
* 7224

{% hint style="success" %}
 **Ans**: Rs 6708

**Explanation:**  
Let the amount received by A, B, C, and D be Rs.3x, 4.x, 9x.and Rs.10x respectively. 

According to the question,  
9x - 4x = 2580  
5x = 2580  
x = 25805 = 516  
Total amount of the money of A and D = 3x + 10x =13x = 13 x 516 = Rs.6708
{% endhint %}

## Technical MCQ

Not using the virtual destructor feature in C++ object-oriented programming can cause ?

* An Issue in creating an object of the class
* Memory leak
* An issue in calling the base class destructor
* None of the above

{% hint style="success" %}
**Ans : \(B\) Memory Leak**

 **Explanation:** Virtual destructor is used to maintain the hierarchy of destructor calls for polymorphic classes in inheritance. If we don't use it then it may cause resource leak or memory leak.
{% endhint %}

## Coding

Given the array nums, obtain a subsequence of the array whose sum of elements is strictly greater than the sum of the non included elements in such subsequence.

If there are multiple solutions, return the subsequence with minimum size and if there still exist multiple solutions, return the subsequence with the maximum total sum of all its elements. A subsequence of an array can be obtained by erasing some \(possibly zero\) elements from the array.

Note that the solution with the given constraints is guaranteed to be unique. Also, return the answer sorted in non-increasing order.

**Example 1:**

```text
Input: 
nums = [4,3,10,9,8] 

Output: 
[10,9]
```

 **`Explanation:`** `The subsequences [10,9] and [10,8] are minimal such that the sum of their elements is strictly greater than the sum of elements not included, however, the subsequence [10,9] has the maximum total sum of its elements.` 

**Example 2:**

```text
Input: 
nums = [4,4,7,6,7] 

Output: 
[7,7,6] 
```

**`Explanation:`**`The subsequence [7,7] has the sum of its elements equal to 14 which is not strictly greater than the sum of elements not included (14 = 4 + 4 + 6). Therefore, the subsequence [7,6,7] is the minimal satisfying the conditions. Note the subsequence has to returned in non-decreasing order.`

### Solution:

{% hint style="success" %}
**Explanation:**

1\)Find the sum of all the elements of the vector.

 2\)Sort the vector in descending order. 

3\)Keep on subtracting the elements from the highest to lowest until the sum of the highest elements is greater than the remaining. Also, add the elements to the answer vector. 

4\)The required elements untill the condition meet is the final answer.

 5\)Return them in non-decreasing order
{% endhint %}

```cpp
class Solution {
public:
    vector<int> minSubsequence(vector<int>& nums) {
        int sum=0,newsum=0;
        vector<int>ans;
        for(int i=0;i<nums.size();i++)
        {
            sum+=nums[i];
        }
        sort(nums.begin(),nums.end(),std::greater<>());
        for(int i=0;i<nums.size();i++)
        {
            newsum+=nums[i];
            sum=sum-nums[i];
            ans.push_back(nums[i]);
            if(newsum>sum)
                break;
        }
        sort(ans.begin(),ans.end(),std::greater<>());
        return ans;
    }
};
```




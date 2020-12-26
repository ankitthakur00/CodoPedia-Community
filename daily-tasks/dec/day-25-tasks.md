---
description: 26-12-2020
---

# Day 26 : Tasks

## Aptitude

The weight of a bucket is 15 kg. When it is filled water upto 53​ of its capacity in weight is 19 kg. If it is filled with water up to 54​th of its capacity. Find the weight of the empty bucket if it is completely filled with water.

* 23
* 15
* 17
* None of the above

{% hint style="success" %}
Ans : 23  
Explanation :  
  


![](https://haygot.s3.amazonaws.com/questions/1150319_866797_ans_146a52b9a0294380b5190f00abe20be4.jpg)
{% endhint %}

## Technical MCQ

[Which of the following is not a member of a class ?](https://gateoverflow.in/44975/which-of-the-following-is-not-a-member-of-a-class)

* Static function
* Friend Function
* const function
* virtual function

{% hint style="success" %}
Ans : Friend function
{% endhint %}

## Coding

Given a list of non-negative integers nums, arrange them such that they form the largest number.

Note: The result may be very large, so you need to return a string instead of an integer.

```text
Example 1:
Input: nums = [10,2]
 Output: "210"

Example 2:
Input: nums = [3,30,34,5,9] 
Output: "9534330" 

Example 3:
Input: nums = [1] 
Output: "1" 
Example 4:
Input: nums = [10]
 Output: "10"
```

### **Solution :**

```cpp
string largestNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end(),[](int a,int b){
            string c=to_string(a);
            string d=to_string(b);
           return (c+d)>(d+c);
        });
        string p="";
        for(int i=0;i<nums.size();i++)
            p+=to_string(nums[i]);
        int i=0;
        while(i<p.size() && p[i]=='0')
            i++;
        if(i==p.size())
            return "0";
        return p.substr(i);
    }
```


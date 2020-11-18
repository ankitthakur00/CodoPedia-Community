---
description: 'Date : 18 November 2020'
---

# Day 17 : Tasks

## Aptitude Question

What is the angle between hands at 10:20? 

1. 180
2. 170
3. 190
4. 160

{% hint style="success" %}
**Ans: 190**

At 10:20 the minute hand is at 4 and it makes an angle of 4\*30 = 120 deg from 12.

At 10:20 the hour hand is between 10 and 11 and it makes an angle of 

10**\***_30+ \(20\*_30\)/60 = 300+10 = 310 deg from 12.

At 10:20 the minute and the hour hands make an angle of 310–120 = 190 deg between them.
{% endhint %}

![](../.gitbook/assets/image%20%281%29.png)

## Technical MCQ

Given a heap with n elements that supports insert and extract-min, which of the following tasks can be achieved in O\(logn\) time? 

1. Finding the median of the elements stored in the heap.
2. Finding the largest element stored in the heap.
3. Finding the fifth-smallest element stored in the heap.
4. None of the given options.

{% hint style="success" %}
**Ans:** Finding the fifth-smallest element stored in the heap.
{% endhint %}

## Coding Question

Given a binary array, find the maximum length of a contiguous subarray with an equal number of 0 and 1.

`Input:` 

```text
[0,1,0] 
```

`Output:`

```text
2
```

 `Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.`

#### `Algorithm:` This is one of the most common interview question. Dry run the algorithm to understand it thoroughly.

{% hint style="success" %}
1. Starting from left of array and keep adding elements to a variable **sum**
2. Add **-1 for 0** and **1 for 1**
3. Now, everytime sum becomes zero, we know all the elements from begining of array have been neutralized , meaning we have got equal number of ones and zeroes, let this occurs at index i, so longestContArray = i+1 \(because we are dealing with indices\)
4. But we are not done yet!, consider the case : \[1,**1,0**,1,1\]

* In this case sum will never become zero,
* but there exists a subarray of length 2, having equal 0 & 1
* let's see the value of sum at index : 1 and 3
* Ohh!! sum = 2 for both indices
* what does this mean???
* **This means that if we get the same sum value for two indices i and j, then all the elements within the range \[i,j\) or \(i,j\] have been neutralized**
* What datastructure can remember the sum and index
* Ofcourse ! Map, so we use a map to store the sum and index values,
* if sum == 0 then we have already solved the cases
* but if sum!=0 and this sum doesn't already exist in the map, then store it with it's corresponding index
* but if sum !=0 and sum already exists in the map then, dependig on whether i - m\[sum\] &gt; LongestContArray, update LongestContArray
* Note we need to store a unique sum value only once, after that whenever we encounter the same sum again our interval length is going to increase only and that is what we want ex- \[1,0,1,0,1\] we get sum = 1 three times we store sum = 1 for index = 0 only and never update it as we want longest length
{% endhint %}

{% tabs %}
{% tab title="Solution.cpp" %}
```cpp
int findMaxLength(vector<int>& nums) {
       int sum=0;
       unordered_map<int,int> m;
       unsigned int longestContArray = 0;
       
        for(int i=0;i<nums.size();i++){
           sum += (nums[i]==0)?-1:1;
           
           auto it = m.find(sum);
           
           if(sum == 0){
              if(longestContArray < i+1)
               longestContArray = i+1;
           }
           else if(it != m.end()){
              if(longestContArray < i-it->second)
               longestContArray = i-it->second;
           }
           else if(it == m.end())
                m.insert({sum,i});
       }
        return longestContArray;
    }
```
{% endtab %}

{% tab title="Solution.java" %}
```java
public class Solution {

    public int findMaxLength(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, -1);
        int maxlen = 0, count = 0;
        for (int i = 0; i < nums.length; i++) {
            count = count + (nums[i] == 1 ? 1 : -1);
            if (map.containsKey(count)) {
                maxlen = Math.max(maxlen, i - map.get(count));
            } else {
                map.put(count, i);
            }
        }
        return maxlen;
    }
}
```
{% endtab %}

{% tab title="Solution.py" %}
```python
def findMaxLength(self, nums: List[int]) -> int:
  
    mp = {0: -1}  
    prefix_sum = 0
    result = 0
    for idx, num in enumerate(nums):
        prefix_sum += 1 if num == 1 else -1
        if prefix_sum in mp:
		         result = max(result, idx - mp[prefix_sum])
        else:
            mp[prefix_sum] = idx
    
    return result
```
{% endtab %}
{% endtabs %}

  





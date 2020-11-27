---
description: 26-11-2020
---

# Day 25 : Tasks

## Aptitude 

Father's age is three times the sum of ages of his two children. After 5 years his age will be twice the sum of ages of two children. Find the age of father.

* 75
* 45
* 66
* 88

{% hint style="success" %}
Ans :  45   
  
Explanation :   
  
Let the age of father =x years  
The sum of the age of 2 children =y years  
According to the first condition  
⇒x=3y.....eq1  
After 5 years  
⇒ Father's age =x+5  
⇒ The sum of ages of his two children =y+10According to the second condition  
⇒x+5=2\(y+10\)⇒x+5=2y+20  
⇒x−2y=15....eq2  
Put the value of x from eq1  
⇒3y−2y=15⇒y=15  
Put  y=15 in eq1  
⇒x=3×15⇒x=45Hence, father age =45 years
{% endhint %}

## Technical MCQ

Suppose a database schedule S involves transactions T1, T2,...Tn. Consider the precedence graph of S with vertices representing the transactions and edges representing the conflicts. If S is serializable, which one of the following orderings of the vertices of the precedence graph is guaranteed to yield a serial schedule?

1. Topological Sort.
2. Ascending order of transactions indices.
3. Breadth first order
4. Depth first order

{% hint style="success" %}
Topological Sort
{% endhint %}

## Coding Question



Given a non-empty array of integers, return the **k** most frequent elements.

**Example 1:**

```text
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```text
Input: nums = [1], k = 1
Output: [1]
```

**Note:**

* You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
* Your algorithm's time complexity **must be** better than O\(n log n\), where n is the array's size.
* It's guaranteed that the answer is unique, in other words the set of the top k frequent elements is unique.
* You can return the answer in any order.

## Solution :



**MaxHeap**

Simply, we can just use map to count each distinct number and then insert them all into a priority\_queue. The time complexity will be O\(klogk\) where k is the number of the distinct numbers.

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) 
    {
        vector<int> v;
        unordered_map<int, int> count_map;
        for(auto n: nums) count_map[n]++;
        priority_queue<pair<int, int>> maxHeap;
        for(auto& pair: count_map) maxHeap.emplace(pair.second, pair.first);
        while(k--)
        {
            v.push_back(maxHeap.top().second);
            maxHeap.pop();
        }
        return v;
    }
};
```

**MinHeap**

Actually, we can also solve this using minimal heap which will remove the least frequent if the size of the minimal heap is larger than k, ensuring the top most k frequent will be stored in the minimal heap in the end.

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) 
    {
        vector<int> v;
        unordered_map<int, int> count_map;
        for(auto n: nums) count_map[n]++;
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int,int>>> minHeap;
        for(auto& pair: count_map) 
        {
            minHeap.emplace(pair.second, pair.first);
            if(minHeap.size() > k) minHeap.pop();
        }
        while(k--)
        {
            v.push_back(minHeap.top().second);
            minHeap.pop();
        }
        return v;
    }
};
```

**Multimap**

Using multimap to sort the numbers by its frequency and to accelerate the collecting process, we can adopt set to collect the frequencies for each number and then collect from the most frequent to the least.

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) 
    {
        vector<int> v;
        unordered_map<int, int> keys_map;
        for(auto n: nums) keys_map[n]++;
        multimap<int,int> count_map;
        set<int> count_set;
        for(auto& pair: keys_map) count_set.insert(pair.second), count_map.emplace(pair.second, pair.first);
        for(auto count_iter=count_set.rbegin(); count_iter!=count_set.rend(); ++count_iter)
        {
            int i = *count_iter;
            if(count_map.count(i))
            {
                for(auto iter = count_map.equal_range(i).first; iter != count_map.equal_range(i).second; ++iter)
                {
                    v.push_back(iter->second);
                    if(v.size() == k) return v;
                }
            }
        }
        return v;
    }
};
```

**Vector**

Actually the previous solution can be simplified with vector but we then have to traverse all the possible frequency instead of that just appear \(count\_set used in the previous solution\).

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) 
    {
        vector<int> v;
        if(nums.empty()) return v;
        unordered_map<int, int> keys_map;
        for(auto n: nums) keys_map[n]++;
        vector<vector<int>> buckets(nums.size()+1);
        for(auto& pair: keys_map) buckets[pair.second].push_back(pair.first);
        for(int i = nums.size(); i; --i)
        {
            for(int j = 0; j < buckets[i].size(); ++j)
            {
                v.push_back(buckets[i][j]);
                if(v.size() == k) return v;
            }
        }
        return v;
    }
};
```

**Array**

Counting the frquency count and through these values, we can swiftly locate the frquency count which separate the top k most frequent numbers from the rest. We cannot use lower\_bound to locate it, because the index and the frequency count is not one-to-one.

So the following method won't work; and arr here is a vector format of cumulative.  
`int kCount = lower_bound(arr.rbegin(), arr.rend(), k)-upper_bound(arr.rbegin(), arr.rend(), 0)+1;`

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) 
    {
        vector<int> v;
        if(nums.empty()) return v;
        int cumulative[nums.size()+1] = {0};
        unordered_map<int, int> keys_map;
        for(auto n: nums) cumulative[keys_map[n]++]++;
        int kCount = 0;
        for(int i = nums.size(); i; --i) if(cumulative[i]>=k) { kCount = i; break; }
        for(auto& pair: keys_map) 
            if(pair.second > kCount) v.push_back(pair.first);
        if(v.size() == k) return v;
        for(auto& pair: keys_map) 
        {
            if(pair.second == kCount) v.push_back(pair.first);
            if(v.size() == k) return v;
        }
        return v;
    }
};
```

##  

##  


---
description: 'Date : 19 November 2020'
---

# Day 18 : Tasks

## Aptitude 

A sum of money is to be divided among A, B, and C in the ratio 2:3:7. If the total share of A B together is Rs.1500 less than C, what is A's share in it? 

* 2000
* 750
* 1000
* 1500

{% hint style="success" %}
**Ans:** 1500

Let the total sum of money be ₹x. Ratio=2:3:7 Let the money received by A, B and C be 2x, 3x,   and 7x respectively.

 According to the question, 

`7x-(2x+3x)=₹1500` 

`7x-5x=1500` 

`2x=1500`

 `A's share = 2x = ₹1500`
{% endhint %}

## Technical MCQ

Which of the following properties are not expected out of a well-designed hash function?

1. The hash function should be easy to store
2. The hash function should spread out every dataset 
3. The Hash function should be easy to compute
4. The Hash function should spread out most data sets

{% hint style="success" %}
**Answer:** The hash function should spread out every data set.

Other options can be achieved from a hash function easily i.e. hash function should be easy to store, it should spread out most of the dataset and it should be easy to compute, but it cannot assure to spread out every dataset because sometimes there are few datasets that are hard to spread be**c**ause of repeating values or our hash function is not able to compute the different value for each information.

Our hash function should compute values in constant time otherwise we can use trees \(they will give O\(logn\) time\), therefore the hash function should be easy to compute. On the other hand, if we take more space to store the hash function then it will take more time to run the hash function, and finally spreading the data set is the main purpose of the hashing but spreading every data set is impossible.
{% endhint %}

## Coding Question

You are given the following:

1. A positive number N
2. `Heights:` A list of heights of N persons standing in a queue 
3. `Infronts :` A list of numbers corresponding to each person \(P\) that gives of persons who are taller than P and standing in front of P

You need to return a list of the actual order of persons’s height.

`Consider that heights will be unique`

**Input :**

```text
 Heights: 5 3 2 6 1 4 
 InFronts: 0 1 2 0 3 2
```

**Output :** 

```text
Actual order is: 5 3 2 1 6 4
```

So, you can see that for the person with height 5, there is no one taller than him who is in front of him, and hence Infronts has 0 for him. For a person with height 3, there is 1 person \( Height: 5 \) in front of him who is taller than him. You can do similar inferences for other people in the list.

### **Solution:**

```cpp
bool cmp(pair<int,int>& a,pair<int,int>& b)
{
    if(a.first>b.first || (a.first == b.first && a.second<b.second))
        return true;
    return false;
}
vector<int> Solution::order(vector<int> &A, vector<int> &B) 
{
    vector<pair<int,int>> arr;
    
    for(int i=0;i<A.size();i++)
        arr.push_back({A[i],B[i]});
        
    sort(arr.begin(),arr.end(),cmp);
    vector<int> ans;
    
    for(int i=0;i<arr.size();i++)
        ans.insert(ans.begin()+arr[i].second,arr[i].first);
        
    return ans;
}
```

\*\*\*\*

\*\*\*\*


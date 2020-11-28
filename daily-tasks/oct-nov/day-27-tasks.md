---
description: 'Date : 28-11-2020'
---

# Day 27 : Tasks

## Aptitude 

Solution X is 10 percent alcohol by volume, and solution Y is 30 percent alcohol by volume. How many milliliters of solution Y must be added to 200 milliliters of solution X to create a solution that is 25 percent alcohol by volume?

A. 250/3   
B. 500/3   
C. 400   
D. 480   
E. 600

{% hint style="success" %}
Ans :  600  
  
Using allegation method as shown in figure below:  
  
![alle.png](https://gmatclub.com/forum/download/file.php?id=26075&sid=4289504a5dc4b41546e474728636493f)  
  
To obtain a 25% alcohol mixture, X & Y are to be mixed in ratio 5:15 = 1:3  
  
X is already 200ml, so Y should be 200\*3 = 600
{% endhint %}

## **Technical MCQ**

Which normal form is a table "customer" in . if it has following characteristics ?  
It has transitive dependencies   
There are no partial Dependencies in it  
There is no column with redundancy in it

* 1NF
* 2NF
* 3NF
* BCNF

{% hint style="success" %}
**Ans :** 2NF
{% endhint %}



## Coding Question

Given an array of integers A of size N and an integer B.  
Array A is rotated at some pivot unknown to you beforehand.  
\(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2 \).  
  
You are given a target value B to search. If found in the array, return its index, otherwise return -1.  
You may assume no duplicate exists in the array.  
NOTE:- Array A was sorted in non-decreasing order before rotation.  
  
Input 1:  
 A = \[4, 5, 6, 7, 0, 1, 2, 3\]  
 B = 4  
Output 1:  
 0  
Explanation 1:  
 Target 4 is found at index 0 in A.  
  
Input 2:  
 A = \[5, 17, 100, 3\]  
 B = 6  
Output 2:  
 -1![](blob:https://web.telegram.org/e07b7393-c65a-4b7f-8044-4893ca9fb5ed)![](blob:https://web.telegram.org/06195abb-fbce-4170-8feb-0b3633560e0a)

## **Solution :**

\*\*\*\*

```cpp
int Solution::search(const vector<int> &A, int B) {
    int n = A.size();
    int low = 0, high = n-1;
    while(low<=high){
        int mid = low + (high-low)/2;
        if(A[mid] == B) return mid;
        else if(A[0]<=A[mid]){//i.e. left part is sorted
            if(A[0]<=B && B < A[mid]) high = mid-1;//B lies on left part
            else low = mid+1;
        }else{//right part is sorted
            if(A[mid] < B && B<=A[n-1]) low = mid+1;//B lies on right part
            else high = mid-1;
        }
    }
    return -1;
}
```


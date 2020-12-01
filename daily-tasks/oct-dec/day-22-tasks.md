---
description: 23-11-20
---

# Day 22 : Tasks

## Aptitude

Find the missing number  2 , 3 , 7 , 8 , 13 , 14 , ?   


* 24 
* 21 
* 18 
* 20

{% hint style="success" %}
Ans : 20
{% endhint %}

## Technical

Which of the following queries can be used to select data from one table and insert it into another?   
 1. SELECT ALL COPY newtable \[IN externaldb\] FROM Table1;  
 2. SELECT  _COPY newtable \[IN externaldb\] FROM Table1;   
3. SELECT_  INTO newtable \[IN externaldb\] FROM Table1;   
4. SELECT ALL INTO newtable \[IN externaldb\] FROM Table1;

{% hint style="success" %}
Ans: _SELECT_  INTO newtable \[IN externaldb\] FROM Table1;   
  
Explanation :  [https://www.w3schools.com/sql/sql\_select\_into.asp](https://www.w3schools.com/sql/sql_select_into.asp)
{% endhint %}

## Coding question 

  
A linked list is given such that each node contains an additional random pointer which could point to any node in the list or `NULL`.

Return a deep copy of the list.  
Given list 1 -&gt; 2 -&gt; 3 with random pointers going from

1 -&gt; 3  
2 -&gt; 1  
 3 -&gt; 1  
You should return a deep copy of the list. The returned answer should not contain the same node as the original list, but a copy of them. The pointers in the returned list should not link to any node in the original input list.

### Solution :

```cpp
unordered_map<RandomListNode*,RandomListNode*>m;
RandomListNode* Solution::copyRandomList(RandomListNode* A) {
    if(!A) return NULL;
    m[A]=new RandomListNode(A->label);
    m[A]->next=copyRandomList(A->next);
    m[A]->random=m[A->random];
    return m[A];
}

```


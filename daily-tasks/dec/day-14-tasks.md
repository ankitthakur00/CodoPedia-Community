---
description: 'Date : 14 December 2020'
---

# Day 14 : Tasks

## Aptitude

Excluding stoppages, the speed of a bus is 54 kmph and including stoppages, it is 45 kmph. For how many minutes does the bus stop per hour? 

* 9
* 10
* 12
* 20

{% hint style="success" %}
**Ans**: \(B\) 10 Km

**Explanation:**

Due to stoppages, it covers 9 km less.

Time taken to cover 9 Km = \(\(9/54\)\*60\) Min

=10 Min.
{% endhint %}

## Technical MCQ

Which of the following is not true about single-row subqueries? 

* Single row subqueries return one row from the inner SELECT statement.
* Single row subqueries return one row from the outer SELECT statement.
* Single row subqueries use single row comparison operators
* All of the abov**e**

{% hint style="success" %}
**Ans:** Single row subqueries return one row from the outer SELECT statement.
{% endhint %}

## Coding

Design a data structure that follows the constraints of a Least Recently Used \(LRU\) cache.

Implement the LRUCache class:

LRUCache\(int capacity\) Initialize the LRU cache with positive size capacity. int get\(int key\) Return the value of the key if the key exists, otherwise return -1. 

void put\(int key, int value\) Update the value of the key if the key exists. 

Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key. 

_**Follow up:** Could you do get and put in O\(1\) time complexity?_

**`Example :`**

```text
Input:
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"] [[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]] 

Output:
 [null, null, null, 1, null, -1, null, -1, 3, 4]
```

{% hint style="info" %}
**`Explanation:`**  ``

`LRUCache lRUCache = new LRUCache(2);` 

`lRUCache.put(1, 1); //cache is {1=1}` 

`lRUCache.put(2, 2); //cache is {1=1, 2=2}` 

`lRUCache.get(1); // return 1` 

`lRUCache.put(3, 3); //LRU key was 2, evicts key 2, cache is {1=1, 3=3}` 

`lRUCache.get(2); // returns -1 (not found)` 

`lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}` 

`lRUCache.get(1); // return -1 (not found)` 

`lRUCache.get(3); // return 3` 

`lRUCache.get(4); // return 4`
{% endhint %}

### Solution :

```cpp
class LRUCache {
public:
   
unordered_map<int,list<pair<int,int>>::iterator>m;
    list<pair<int,int>>l;
int p;
LRUCache(int capacity) {
p=capacity;
}
void move(int key,int value)
{
        l.push_front({key,value});
        l.erase(m[key]);
        m[key]=l.begin();
}
int get(int key) {
if(m.count(key))
    {
      int v=(*m[key]).second;
        move(key,v);
        return v;
    }
    else
    return -1;
}

void put(int key, int value) {
 if(m.count(key))
    {
        move(key,value);
    }
    else 
    {
        l.push_front({key,value});
            m[key]=l.begin();
            if(l.size()>p)
            {
                m.erase(l.back().first);
                l.pop_back();
            }
    }
}
```


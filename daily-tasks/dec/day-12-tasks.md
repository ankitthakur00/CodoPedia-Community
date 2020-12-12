---
description: 'Date : 12 December 2020'
---

# Day 12 : Tasks

## Aptitude

If Friday falls on the 15th of September 2000 what will be the day of the 15th of September 2001? 

* Thursday
* Friday
* Saturday
* Sunday

{% hint style="success" %}
**Ans:** Saturday

**Explanation:**

15th September 2001 will be a Saturday.

For any given day of the year and any other day of the year, if their difference is a multiple of 7, they have the same day otherwise it is shifted.

**Example:** for 1st January of a normal year, the last day is 31st December which is the 365th day.

365-1 = 364 which is 7 x 52.

Hence the last day of a normal year has the same day as the first day.

Hence the first day of the next year has its day shifted by 1.

However**,** as a leap year has 366 days it is shifted by 2 in that case.

2000 is a leap year however the extra day was Feb 29 which I already counted.

Hence as 15th Sep 2000 and 2001 have 364 days in between them, the day in 2001 will be shifted by 1 hence it will be a Saturday.

\*\*\*\*
{% endhint %}

## Technical MCQ

 Which of the following statement is not true? 

* A pointer to an int and a pointer to double is of the same size.
* A pointer must point to a data item on the heap \(free store\).
* A pointer can be reassigned to point to another data item.
* A pointer can point to an array.

{% hint style="success" %}
**Ans:** \(b\) A pointer must point to a data item on the heap \(free store\).
{% endhint %}

## Coding

Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**`Input`**:

```text
 strs = ["eat","tea","tan","ate","nat","bat"] 
```

**`Output:`** 

```text
[["bat"],["nat","tan"],["ate","eat","tea"]]
```

### Solution :

```cpp
vector<vector<string>> groupAnagrams(vector<string>& strs) {
        map<string,vector<string>>m;
        for(int i=0;i<strs.size();i++)
        { string k=strs[i];
            sort(k.begin(),k.end());
            m[k].push_back(strs[i]);
        }
        vector<vector<string>>v;
        for(auto itr:m)
            v.push_back(vector<string>(itr.second.begin(),itr.second.end()));
        return v;
    }
```




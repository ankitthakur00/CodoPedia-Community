---
description: 'Date : 8 November 2020'
---

# Day 10 : Tasks

## Aptitude

Out of the total production of iron from hematite, an ore of iron, 20% of the ore gets wasted, and out of the remaining iron, only 25% is pure iron. If the pure iron obtained in a year from a mine of hematite is 80,000kg, then what will be the quantity of hematite mined in the year.

1. 5,00,000 Kg.
2. 4,00,000 Kg.
3. 4,50,000 Kg.
4. None of these.

{% hint style="success" %}
Let 100 kg of hematite be obtained then 20% of it gets wasted which means 80 kg of ore remains. Pure iron = 25% of remaining ore = 8025/100 = 20 kg. 20 kg pure Iron is obtained from 100 of hematite. 1 kg pure Iron is obtained from = 100/20 hematite; Then, 80000 kg pure Iron is obtained from = \(100/20\)80000 = 400000 kg hematite.

So , **Option \(B\)** 4,00,000 kg is the right answer
{% endhint %}

## Technical MCQ

 Consider an array of length 5 arr\[\]={9,7,4,2,1} .What are the steps of insertions done while running insertion sort on the array? 

1. 7 9 4 2 1 4 7 9 2 1 2 4 7 9 1 1 2 4 7 9
2. 7 4 2 1 9 4 2 1 9 7 2 1 9 7 4 1 9 4 7 2
3. 9 7 4 1 2 9 7 1 2 4 9 1 2 4 7 1 2 4 7 9
4. None of these.

{% hint style="success" %}
**Ans :** 7 9 4 2 1 4 7 9 2 1 2 4 7 9 1 1 2 4 7 9
{% endhint %}

## Coding Question

> Asked in CodeNation

Given a string, Your task is to return the largest string, based on dictionary order, that can be obtained by erasing a certain number of characters from the string. For two strings x and y, each consisting of m characters, x is larger than y based on dictionary order, when the first j-1 letters in x and y are equal, where 1&lt;=h&lt;=m but the jth letter in x is larger than the jth letter in y .for example “caa” is larger than “baa”, and “abza” is larger than “abqa”.

`Example : Let the string s, be “baca”. The number of characters to be erased k is 1. There are 4 possible ways of deleting exactly one character from that string “aca”, “bca”,”baa”, and “bac”.Among these strings, “bca” is largest in dictionary order . Thus “bca” is the desired answer.`

**Constraints:**

1&lt;=n&lt;=10^6

0&lt;=k&lt;n

`string contains only English lowercase letters`

**Input Format:** The first line contains a single integer k, denoting the number of characters to erase. In the second line, there is a single string s, denoting the string to erase the characters from. 

**Ouput Format:** Output the resultant string.

**Solution:**

```cpp
string Solve(string s){
     int i;
    set<int> st;
    st.insert(0);
    for(i=1;i<s.length();i++){
        while(st.size()>0 and k>0){
            auto it = st.end();
            it--;
            if(s[*it]<s[i]){
                st.erase(*it);
                k--;
            }
            else
            break;
        }
        st.insert(i);
    }
    while(k>0){
        auto it = st.end();
        it--;
        st.erase(it);
        k--;
    }
    string result="";
    for(auto it=st.begin();it!=st.end();it++)
    {
        result.push_back(s[*it]);
    }
    return result;
    }
```


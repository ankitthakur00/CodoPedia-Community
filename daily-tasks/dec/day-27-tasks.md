---
description: 'Date: 27 December 2020'
---

# Day 27: Tasks

## Aptitude

The ratio of radii of two cylinders is 1:2 and heights are in the ratio 2:3. The ratio of their volumes is 

* 1/3
* 1/6
* 4/9
* 8/27

{% hint style="success" %}
**Ans:** 1/6
{% endhint %}

![](../../.gitbook/assets/capture%20%283%29.png)

## Technical MCQ

Which of the following statements is false? 

* a small page size causes large page tables
* internal fragmentation is increased with small pages
* large page size cause instructions and data that will not be referenced brought into primary storage
* I/O transfers are more efficient with large pages
* None of the above

{% hint style="success" %}
**Ans:** Internal fragmentation is increased with small pages
{% endhint %}

## Coding

You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position. The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess could be rearranged such that they become bulls. Given the secret number secret and your friend's guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows.

 Note that both secret and guess may contain duplicate digits.

**Example 1:**

```cpp
Input: 
secret = "1807", guess = "7810" 

Output:
 "1A3B"
```

 **`Explanation:`**`Bulls are connected with a '|' and cows are underlined: "1807" | "7810"` 

**Example 2:**

```cpp
Input: 
secret = "1123", guess = "0111" 

Output: 
"1A1B" 
```

**`Explanation:`** `Bulls are connected with a '|' and cows are underlined: "1123" "1123" | or | "0111" "0111" Note that only one of the two unmatched 1s is counted as a cow since the non-bull digits can only be rearranged to allow one 1 to be a bull.`

 **Example 3:**

```cpp
Input: 
secret = "1", guess = "0" 

Output: 
"0A0B"
```

 **Example 4:**

```cpp
Input: 
secret = "1", guess = "1" 

Output: 
"1A0B"
```

### Solution:

```cpp
string getHint(string s, string g) {
        unordered_map<char,int>m;
           int a=0,b=0;
        for(int i=0;i<s.size();i++)
        {
            if(s[i]==g[i])
                a++;
            else
            m[s[i]]++;
        }
        for(int i=0;i<g.size();i++)
              {
                 if(s[i]!=g[i] && m[g[i]])
                  { b++;
                   m[g[i]]--;
                   if(m[g[i]]==0)
                    m.erase(g[i]);
                  }
              }
              return to_string(a)+"A"+to_string(b)+"B";
        
    }
```


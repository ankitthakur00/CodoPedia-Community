---
description: 'Date : 16 December 2020'
---

# Day 16 : Tasks

## Aptitude

A train travels 40% faster than a car. Both start from point A at the same time and reach point B, 140km away at the same time. On the way, the train takes 25 minutes for stopping at the stations. What is the speed \(in km/hr\) of the train? 

* 67
* 134.4
* 145.9
* 160

{% hint style="success" %}
**Ans:** 134.4
{% endhint %}

![](../../.gitbook/assets/capture%20%282%29.png)

## Technical MCQ

How many catch blocks you can use with a single Try block? 

* only 2
* only 1
* Maximum 256
* As many as required

{% hint style="success" %}
**Ans :** You can use As many as required catch block with a single Try Block
{% endhint %}

## Coding

The i-th person has weight people\[i\], and each boat can carry a maximum weight of limit.

Each boat carries at most 2 people at the same time, provided the sum of the weight of those people is at the most limit.

Return the minimum number of boats to carry every given person. \(It is guaranteed each person can be carried by boat.\)

**Example 1:**

```text
Input: 
people = [1,2], limit = 3 

Output: 
1
```

 **`Explanation:`**`1 boat (1, 2)`

 **Example 2:**

```text
Input: 
people = [3,2,2,1], limit = 3 

Output:
3
```

 ``**`Explanation:`** `3 boats (1, 2), (2) and (3)`

### Solution:

{% tabs %}
{% tab title="Code" %}
```cpp
int numRescueBoats(vector<int>& people, int limit) {
        sort(people.begin(), people.end());
        int i = 0, j = people.size() - 1;
        int ans = 0;

        while (i <= j) {
            ans++;
            if (people[i] + people[j] <= limit)
                i++;
            j--;
        }

        return ans;
    }
```
{% endtab %}

{% tab title="Explanation" %}
If the heaviest person can share a boat with the lightest person, then do so. Otherwise, the heaviest person can't pair with anyone, so they get their own boat.

The reason this works is that if the lightest person can pair with anyone, they might as well pair with the heaviest person.
{% endtab %}
{% endtabs %}


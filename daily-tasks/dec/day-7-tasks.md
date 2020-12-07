---
description: 07-12-2020
---

# Day 7: Tasks

## Aptitude

Sum of the first 25 terms in AP is 525, the sum of the next 25 terms is 725, what is the common difference?

1. 2/25
2. 4/25
3. 6/25
4. 8/25

{% hint style="success" %}
Ans: 8/25

Explanation:

Sum of the first 25 terms in AP is 525

S₂₅ = \(25/2\)\[\(2a+\(25–1\)d\)\]

525 = 25a+\(25\)12d

21=a+12d ——\(1\)

Sum of the next 25 terms is 725

Sum of next 25 terms \(S₂₅’ \)= Sum of 50 terms-Sum of first 25 terms

S₅₀= \(50/2\)\[2a+\(49d\)\]

S₅₀= 50a+1225d

S₂₅’ = S₅₀-S₂₅ = 50a+1225d-525

725 = 50a+1225d-25a-300d

725 = 25a+925d

29= a+37d—-\(2\)

Solving for a and d from \(1\) and \(2\),

d=8/25
{% endhint %}

## Technical

We cannot create instance of:

1. Anonymous Class
2. Nested Class
3. Parent Class
4. Abstract Class

{% hint style="success" %}
Ans: Abstract Class
{% endhint %}

## Coding Question

Given an string A. The only operation allowed is to insert characters in the beginning of the string.

Find how many minimum characters are needed to be inserted to make the string a palindrome string. 

```text
Input 1:
    A = "ABC"
Output 1:
    2
    Explanation 1:
        Insert 'B' at beginning, string becomes: "BABC".
        Insert 'C' at beginning, string becomes: "CBABC".

Input 2:
    A = "AACECAAAA"
Output 2:
    2
    Explanation 2:
        Insert 'A' at beginning, string becomes: "AAACECAAAA".
        Insert 'A' at beginning, string becomes: "AAAACECAAAA".
```

## Solution:

```cpp
int Solution::solve(string A) {
    int n = A.length();
    int match = 1;
    if (n == 0)
    {
        return 0;
    }
    for(int i = 1 ; i < n; i++)
    {
        int start = 0 ;
        int end = i;
        int p = 1;
        while(start<end)
        {
            if (A[start] != A[end])
            {
                p = 0;
                break;
            }
            end--;
            start++;
        }
        if(p == 1)
        {
            match = i+1;
        }
    }
    return n - match;
}
```

{% hint style="success" %}
Explanation :

Each index of LPS array contains the longest prefix which is also a suffix. Now take the string and reverse of a string and combine them with a sentinel character in between them and compute the LPS array of this combined string. Now take the last value of the LPS array and subtract it with the length of the original string, This will give us the minimum number of insertions required in the beginning of the string .
{% endhint %}


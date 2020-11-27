---
description: 17-11-2020
---

# Day 16 : Tasks

## Aptitude

The sum of three from the four numbers A,B,C,D are 4024,4087,4524,and 4573.What is the largest of the numbers A,B,C,D.

1. 1650
2. 1164
3. 1712
4. 1211

{% hint style="success" %}
Answer: 1712

Equations are A+B+C=4024 A+B+D=4087 A+C+D=4524 B+C+D=4573 solving LAST 2 EQUATIONS WE GET B=A+49 USING IT IN 2ND EQ WE GET 2A+D=4038..\(i\) SUBTRACTING LAST EQUATION FROM 1ST EQ WE GET A-D=-549..\(ii\) SOLVING \(i\) ND \(ii\) WE GET A=1163 USING A WE GET D=1712. SO 1712 IS THE ANS
{% endhint %}

## Technical

Consider the following 2 tables named Toys and Category with their respective columns. In SQL server, which of the following queries is used to display the toy names and their respective categories?

Schema: Toys\(ToyId, VToyName, CategoryId\)

 Category\(cCategoryID, cCategory\)

1. Select t.vToyName, c.cCategory from Toys t join category c on t.cCategoryID=c.CategoryId
2. select vToyName, cCategory from Toys join Category on CategoryId=cCategoryID
3. select t.vToyName, c.cCategory from Toys t join Category c
4. select t.vToyName, c.cCategory from Toys t, Category c on cCategoryId=cCategoryID

{% hint style="success" %}
Answer: select vToyName, cCategory from Toys join Category on CategoryId=cCategoryID
{% endhint %}

## Coding Question

Given an encoded string, return its decoded string. The encoding rule is: k\[encoded\_string\], where the encoded\_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there won't be input like 3a or 2\[4\].

```text
Input: s = "2[abc]3[cd]ef"

Output: "abcabccdcdcdef"
```

## Solution:

```cpp
string decodeString(string s) {
        stack<string> chars;
        stack<int> nums;
        string res;
        int num = 0;
        for(char c : s) {
            if(isdigit(c)) {
                num = num*10 + (c-'0');                              
            }
            else if(isalpha(c)) {
                res.push_back(c);                
            }
            else if(c == '[') {
                chars.push(res);
                nums.push(num);
                res = "";
                num = 0;
            }
            else if(c == ']') {
                string tmp = res;
                for(int i = 0; i < nums.top()-1; ++i) {
                    res += tmp;
                }
                res = chars.top() + res;
                chars.pop(); 
                nums.pop();
            }
        }
        return res;
 }
```


---
description: 'Date : 4 November 2020'
---

# Day 6: Tasks

## Aptitude

Five years ago the average age of a family of 3 members was 27 years. A child has Been born, due to which the average age of the family is 25 years today. What is the Present age of the child?

1. 5 
2. 6 
3. 4 
4. 7

{% hint style="success" %}
**Ans :** 4

Five years ago the average age of a family of 3 members was 27 years.

total = 27\*3=81

now= 81 + 3\*5=96

again 25\*4=100

therefore, 100-96 = 4 
{% endhint %}

## Technical MCQ

which of the following is true about the declaration and the defination of a variable?

1. Both can occur multiple times, But declaration must occur first.
2. There is no difference between them.
3. A Defination occurs once, But declaration may occur multiple times.
4. A Declaration occurs once ,But defination may occur multiple times.
5. Both can occur multiple times, But a defination must occur first.

{% hint style="success" %}
**Ans :** A Declaration occurs once ,But defination may occur multiple times.

Declaration of a variable is for informing to the compiler the following information: name of the variable, type of value it holds and the initial value if any it takes. i.e., declaration gives details about the properties of a variable. Whereas, Definition of a variable says where the variable gets stored. i.e., memory for the variable is allocated during the definition of the variable.
{% endhint %}

## Coding Question

You are given an array `coordinates`,`coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

![](../../.gitbook/assets/untitled-diagram-2.jpg)

```text
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```

**Solution:**

> **The basic line equation idea.** 
>
> \(y-y1\)\(x2-x1\) = \(y2-y1\)\(x-x1\) 
>
> **or**
>
>  y-y1 = \(\(y2-y1\)/\(x2-x1\)\) \(x-x1\)



```cpp
bool checkStraightLine(vector<vector<int>>& cd) {
        int y_diff=(cd[1][1]-cd[0][1]),x_diff=(cd[1][0]-cd[0][0]);
        for(int i=2;i<cd.size();i++)
            if((cd[i][1]-cd[0][1])*x_diff != (cd[i][0]-cd[0][0])*y_diff)   
            return false;
        return true;
    }
```


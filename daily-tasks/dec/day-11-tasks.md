---
description: 'Date : 11 December 2020'
---

# Day 11 : Tasks

## Aptitude

Anish had a certain amount with him. He spent 20% of that to buy a new cell phone and 15% of the remaining on buying a laptop. Then he donated Rs. 160 in a temple. If he is left with Rs. 1,200, how much did he buy the laptop for? 

* 220
* 240
* 320
* 350

{% hint style="success" %}
**Ans:** Rs. 240 

**Explanation:** 

Let Anish had a total amount = Rs. x. 

Then, Money spent on buying the cellphone = 20% of x = \(20/100\) \* x = Rs. x/5 

Now, remaining amount = x - \(x/5\) = 4x/5

Money spent on buying the laptop = 15% of \(4x/5\) = \(15/100\) \* \(4x/5\) = Rs. 3x/25 

Then, he donated Rs. 160 in a temple and left with Rs. 1200.

Therefore, Total amount he had = Money spent on buying the cellphone + Money spent on buying the laptop + Money donated in a temple + Money left with him

 x = \(x/5\) + \(3x/25\) + 160 + 1200

x - \(x/5\) - \(3x/25\) = 1360 

 \(25x - 5x - 3x\)/25 = 1360

 17x = 1360\*25 

x = \(1360/17\) \*25 

x = 80 \*25 , x = 2000 

Thus, Total amount Anish had = Rs. 2000 

Now, the amount he buy the laptop for = Rs. 3x/25 = \(3  2000\)/25 = 3 \* 80 = **Rs. 240**
{% endhint %}



## Technical MCQ

Which of the following type of class allows only one object of it to be created? 

* Virtual class
* Abstract Class
* Singleton class
* Friend class

{% hint style="success" %}
**Ans:** \(c\) Singleton class

**Explanation:** Singleton is a design pattern. It ensures that only one instance of a class is created.

Read More [https://www.programiz.com/java-programming/singleton](https://www.programiz.com/java-programming/singleton)
{% endhint %}

## Coding 

There is a robot starting at position \(0, 0\), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot ends up at \(0, 0\) after it completes its moves.

The move sequence is represented by a string, and the character moves\[i\] represents its ith move. Valid moves are R \(right\), L \(left\), U \(up\), and D \(down\). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

**`Note:`** `The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.`

**Example 1:**

```text
Input: 
moves = "UD" 

Output: 
true
```

**Explanation:** The robot moves up once, and then down once. All moves have the same magnitude, so it ended up at the origin where it started. Therefore, we return true.

**Example 2:**

```text
Input: 
moves = "LL" 

Output: 
false 
```

**Explanation:** The robot moves left twice. It ends up with two "moves" to the left of the origin. We return false because it is not at the origin at the end of its moves.

### Solution :

```cpp
bool judgeCircle(string moves) {
        int u=0,r=0;
        for(int i=0;i<moves.size();i++)
            if(moves[i]=='U')
                u++;
            else if(moves[i]=='R')
                r++;
            else if(moves[i]=='L')
                r--;
        else
            u--;
        if(u==0 && r==0)
            return true;
        return false;
    }
```


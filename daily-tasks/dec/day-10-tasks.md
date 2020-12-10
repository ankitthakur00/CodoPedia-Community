---
description: 10 December 2020
---

# Day 10 : Tasks

## Aptitude

You have 59 cubic blocks. What is the minimum number that needs to be taken away in order to construct a solid cube with none left over?

1. 31
2. 32
3. 33
4. 34

{% hint style="success" %}
Ans: 32

Explanation:

1\*1\*1=1

2\*2\*2=8

3\*3\*3=27

4\*4\*4=64. Oops, larger than 59.

So we need only 27 blocks.

That means that we can take away 59–27=32 blocks.
{% endhint %}

## Technical

Which of the following does not interrupt the running process?

1. Time Interrupt
2. Device
3. Power Failure
4. Scheduler Process

{% hint style="success" %}
Answer: \(b\) Scheduler process

Explanation: Scheduler process does not interrupt in any running process. Its job is to select the processes for long-term, short-term, and short-term scheduler.
{% endhint %}

## Coding Question

You will be given a 2-D array a\[ \]\[ \] of size n \* n which represents positions in a golf course. A golfer wants to start from the top left corner and reach the bottom right corner of the golf course with any number of shots. Your task is to analyse the 2-D array and determine whether it is possible or not.

The 2-D array has a whole number in each cell. The number represents the maximum distance, a shot taken from that cell can reach. Shots can be taken in any of the 4 directions - UP, RIGHT, DOWN and LEFT. For example if a\[i\]\[j\] hold a value 'x', then the golfer can go to any cell between a\[i-x\]\[j\] and a\[i+x\]\[j\] or between a\[i\]\[j-x\] and a\[i\]\[j+x\] from that cell. If a cell holds the value 0, that cell is a dead end. The golfer cannot go anywhere if he reaches there.

Your task: Your task is to complete the function is\_possible\(\). This function gets the 2-D array a\[ \]\[ \] and its number of rows n as argument. Return 1 if it is possible to start from top left and reach bottom right, else return 0. Returned value will be printed y driver code.

```text
Example: 
Input:
2
4
3 0 0 2 0 2 1 1 1 0 0 0 0 4 0 0
3
1 2 0 0 0 2 3 0 1

Output:
1
0

```

```text
Explanation:
Testcase 1:
3 0 0 2
0 2 1 1
1 0 0 0
0 4 0 0
We can see the path a[0][0] -> a[0][3] -> a[1][3] -> a[1][2] -> a[1][1] -> a[3][1] -> a[3][3], hence output is 1
```

```text
Testcase 2:
1 2 0
0 0 2
3 0 1
​There is no possible path to reach the bottom right cell, hence output is 0.
```

## Solution:

```cpp
bool is_possible(int** a, int n)
{
    queue<pair<int,int>>q;
    q.push({0,0});

    while(!q.empty())
    {
        pair<int,int> p=q.front();
        q.pop();
        int r=a[p.first][p.second];
        a[p.first][p.second]=0;
        int x=p.first;
        int y=p.second;
     
        if((x==n-1 && y+r>=n-1) || (y==n-1 && x+r>=n-1))  return true;
        for(int i=y+1;i<=y+r && i<n;i++)
         if(a[x][i]) q.push({x,i});
        
        for(int i=y-1;i>=y-r && i>=0;i--)
         if(a[x][i]) q.push({x,i});
         
        for(int i=x+1;i<=x+r && i<n;i++)
         if(a[i][y]) q.push({i,y});
         
        for(int i=x-1;i>=x-r && i>=0;i--)
         if(a[i][y]) q.push({i,y});
    }
    return false;
}
```


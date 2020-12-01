---
description: 'Date: 02 November 2020'
---

# Day 4: Tasks

## Puzzle

You have 12 balls identical in every way except that one of them weighs slightly less or more. You have a balance scale. Find the Minimum number of comparisons to find the defected ball.

1. 3 
2. 4 
3. 5 
4. 6

{% hint style="success" %}
**Ans** : 3
{% endhint %}

{% page-ref page="../../blog/tricky-puzzle-1-12-balls.md" %}



## Technical MCQ

In SQL which of the following is used to improve the query performance. 

1. Triggers 
2. Stored Procedure 
3. Views 
4. Batches

{% hint style="success" %}
**Ans**: Views  
A SQL View is a virtual table backed by a SQL query. It carries much of the same functionality that a table has, but it's backed by a query, rather than a table in the database, and depending on how you have it set up, can pull in a wide variety of data.  
{% endhint %}

## Coding Question

Given a non-empty 2D array `grid` of 0's and 1's, an **island** is a group of `1`'s \(representing land\) connected 4-directionally \(horizontal or vertical.\) You may assume all four edges of the grid are surrounded by water.

Find the maximum area of an island in the given 2D array. \(If there is no island, the maximum area is 0.\)

> Example:

```text
[ [0,0,1,0,1],
 [0,0,1,1,1],
 [0,0,0,0,1],
 [0,1,1,1,0],
 [0,1,1,0,0]]
```

> Output:

```text
6
```

> Given the above grid, return 6. Note the answer is not 11, because the island must be connected 4-directionally.

**Solution:**

```cpp
//Global Declaration
int maxSize = 0; 
int x[4] = {1, 0, -1, 0};
int y[4] = {0, -1, 0, 1};
    
void dfs(int i, int j, int m, int n, vector<vector<int>>& grid, vector<vector<bool>>& visited) 
{
        if (i < 0 || i > m-1 || j < 0 || j > n-1 || visited[i][j] || grid[i][j] == 0) return;
        visited[i][j] = true;
        maxSize++;
        for (int k=0; k<4; k++) {
            dfs(i+x[k], j+y[k], m, n, grid, visited);
        }
}
```

\*\*\*\*




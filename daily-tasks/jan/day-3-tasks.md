---
description: 'Date : January 3 , 2021'
---

# Day 3 : Tasks

## Aptitude

If \* stands for /   
/ stands for -  
- stands for +   
+ stands for \*  
Then 9/8\*7+5-10=?  
a\)   13.3  
b\)   10.8  
c\)   10.7  
d\)   6.12

{% hint style="success" %}
Answer : 13.3  
∗ stands for /  
/ stands for −  
+ stands for ∗  
− stands for +  
Therefore, given question is equivalent to   
9 − 8 / 7 ∗ 5 + 10   
= 9 − 1.14 ∗ 5 + 10   
= 9 − 5.7 + 10   
= 3.3 + 10 = 13.3
{% endhint %}

## Technical

Guess output of below code snippet :  


```cpp
#include<iostream> 
  
using namespace std; 
int N = 10; 
  
int main() 
{ 
  static int x = 1; 
  if (cout << x << " " && x++ < N && main()) 
  { } 
  return 0; 
}
```

{% hint style="success" %}
Output :

```text
1 2 3 4 5 6 7 8 9 10
```
{% endhint %}

## Coding

Have the function, SearchingChallenge\(strArr\) take the array of integers stored in strArr, which will be a N\*M Matrix of positive single digit integers, and find the longest increasing path composed of distinct integers. When moving through the matrix you can only go up,down,left and right.

**Example:**   
_Input1:_   
strArr = \["345" , "326" , "221"\]

_Output1 :_   
3

_Explanation1:_   
Matrix is like  
3 4 5   
3 2 6  
2 2 1  
Path is 3-&gt;4-&gt;5-&gt;6   
No of connections = 3

_Input2:_   
strArr = \["12256" , "56219" , "43215"\]

_Output2 :_  
5

_Explanation2:_   
Matrix is like   
1 2 2 5 6   
5 6 2 1 9   
4 3 2 1 5   
Path is 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;6   
No of connections = 5

### Solution

```cpp
int r=0;
    vector<int>x,y;
    vector<vector<int>>dp;
    bool check(int i,int j,string matrix[],int n)
    {
      if(i<0 || j<0 || i>=n || j>=matrix[0].size())
            return 0;
        return true;
    }
    int dfs(string matrix[],int i,int j,int n)
    {
       
        int p=0;
        if(dp[i][j]!=-1)
            return dp[i][j];
        for(int k=0;k<4;k++)
            if(check(i+x[k],j+y[k],matrix,n) && matrix[i+x[k]][j+y[k]]>matrix[i][j])
                p=max(p,dfs(matrix,i+x[k],j+y[k],n)+1);
        r=max(r,p);
        return dp[i][j]=p;
    }
    int SearchingChallenge(string matrix[],int n) {
      if(n==0)
          return 0;
          x={-1,0,0,1};
          y={0,-1,1,0};
        dp.resize(n,vector<int>(matrix[0].size(),-1));
        for(int i=0;i<n;i++)
       {
           for(int j=0;j<matrix[0].size();j++)
               r=max(r,dfs(matrix,i,j,n));
       }
        return r;
    }
```


---
description: 'Date : 10 November 2020'
---

# Day 12 : Tasks

## Aptitude

 In a group of cows and ducks, the number of legs is 24 more than twice the number of heads. What is the number of cows in the group? 

* 8
* 10
* 12
* 14

{% hint style="success" %}
Answer = 12  
Let "L" = total no. of legs.   
Let "H" = total no. of heads.   
------------------------------------------------------------------  
L = 2H + 24   
Number of legs = 4c + 2d where c = Number of cows and d = Number of ducks   
Number of heads = c + d   
Now   
H=c+d   
L=4c+2d   
Equations:  
 Since L = 2H + 24,   
4c + 2d = 2\(c+d\) + 24   
4c+2d = 2c+2d+24   
2c = 24   
C = 12 \(Number of cows\)
{% endhint %}

## Technical

Which of the below statement\(s\) is/are true about instance variables?   
1. These variables are declared inside a class but outside any method/constructor/any block. They are also referred to as fields.   
2. Objects stores their individual states in this field. Their values are unique to each object\(instance of a class\) and hence they are called instance variables.  
a\) only 1  
b\) only 2  
c\) both 1 and 2  
d\) None

{% hint style="success" %}
Answer : Both 1 and 2
{% endhint %}

## Coding Question

There are N piles of stones arranged in a row. The i-th pile has stones\[i\] stones. A move consists of merging exactly K consecutive piles into one pile, and the cost of this move is equal to the total number of stones in these K piles.   
Find the minimum cost to merge all piles of stones into one pile. If it is impossible, return -1.   


```text
Input: stones = [3,2,4,1], K = 2 
Output: 20 
Explanation: 
We start with [3, 2, 4, 1]. We merge [3, 2] for a cost of 5, 
and we are left with [5, 4, 1]. 
We merge [4, 1] for a cost of 5, and we are left with [5, 5]. 
We merge [5, 5] for a cost of 10, and we are left with [10]. 
The total cost was 20, and this is the minimum possible.
```

### Solution

```cpp
vector<int>sum;
    int piles;
    int dp[101][101][31];
    int cal(int i,int j,int k)
    {
        if(i==j)
        {
            if(k==1) return 0 ;
            return 999999;
        }
        if(k==1)
            return dp[i][j][k]= cal(i,j,piles)+sum[j]-sum[i-1];
        if(dp[i][j][k]!=-1)
            return dp[i][j][k];
        int ans=999999;
        for(int l=i;l<j;l++)
        ans=min(ans,cal(i,l,k-1)+cal(l+1,j,1));
        return dp[i][j][k]=ans;
    }
    int mergeStones(vector<int>& s, int k) {
        if((s.size()-1)%(k-1)!=0)
            return -1;
        memset(dp,-1,sizeof dp);
        piles=k;
        sum.resize(s.size()+1,0);
        for(int i=1;i<=s.size();i++)
            sum[i]+=sum[i-1]+s[i-1];
        return cal(1,s.size(),1);
    }
```

>


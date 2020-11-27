---
description: 'Date : November 7,2020'
---

# Day 9 : Tasks

## Aptitude

Cory has 6 times as many cookies as mike. Phil has half as many as Judy. Judy has half as many as cory. Mike has  6 cookies. How many cookies does Phil have?  
1. 6  
2. 9  
3. 15  
4. 12  


{% hint style="success" %}
Ans. 9 cookies  
Mike has 6 cookies. \(Given\)

Cory has 6 times as many cookies as Mike

⇒ Cory = 6 x 6 = 36 cookies

Judy has half as many as Cory

⇒ Judy = 1/2 x 36 = 18 cookies

Phil has half as many as Judy

⇒ Phil = 1/2 x 18 = 9 cookies
{% endhint %}

## Technical Question

Which phase of the compiler is responsible for validating grammar?  
1. Code Optimization  
2. Syntax Analysis  
3. Semantic Analysis  
4. None of these  

{% hint style="success" %}
 Answer: Syntax Analysis  
Syntax Analysis or Parsing is the second phase, i.e. after lexical analysis. It checks the syntactical structure of the given input, i.e. whether the given input is in the correct syntax \(of the language in which the input has been written\) or not. It does so by building a data structure, called a Parse tree or Syntax tree. The parse tree is constructed by using the pre-defined Grammar of the language and the input string. If the given input string can be produced with the help of the syntax tree \(in the derivation process\), the input string is found to be in the correct syntax. if not, an error is reported by the syntax analyzer.

The Grammar for a Language consists of Production rules.
{% endhint %}

## Coding Question

A 2D matrix represents the cross-section of a nuclear reactor. Different types of elements are present in this reactor. The values present in the matrix represent the element type present in that cell in the cross-section.

Find the size \(in the number of cells occupied\) of the largest contiguous part of the cross-section that consists of a single element type. Continuity is an edge to edge \(that is, it is considered continous only if horizontal or vertical neighbors of the cell consists of the same element.   
Note: The element type can be represented by any positive integer.

```text
Input:

4 4
1 2 3 4
1 2 4 1
1 4 3 2
1 1 7 8

Output:
5
Explanation: The size of the largest continous part is 5 which is (0,0)->(1,0)->(2,0)->(3,0)->(3,1)
```

### Solution\(C++\)

```cpp
#include <bits/stdc++.h>
using namespace std;
void dfs(vector<int> adj[],int i,int j,int val,vector<vector<bool>> &visited,int &cur,int &n,int &m)
{
    
    cur++;
    visited[i][j]=true;
    int row[]={0,0,1,-1};
    int col[]={1,-1,0,0};
    
    for(int k=0;k<4;k++)
    {
        int r=row[k]+i;
        int c=col[k]+j;
        if(r>=0&&c>=0&&r<n&&c<m&&!visited[r][c]&&adj[r][c]==val)
        dfs(adj,r,c,val,visited,cur,n,m);
    }
}
int main() {
	int n,m;
	cin>>n>>m;
	
	vector<int> arr[n];
	
	for(int i=0;i<n;i++)
	{
	    for(int j=0;j<m;j++)
	    {
	        int tmp;
	        cin>>tmp;
	        arr[i].push_back(tmp);
	    }
	}
	
	vector<vector<bool>> visited(n,vector<bool>(m,false));
	int ans=0;
	for(int i=0;i<n;i++)
	{
	    for(int j=0;j<m;j++)
	    {
	        int cur=0;
	        if(!visited[i][j])
	        {
	            dfs(arr,i,j,arr[i][j],visited,cur,n,m);
	            ans=max(cur,ans);
	        }
	    }
	}
	cout<<ans;
	return 0;
}
```


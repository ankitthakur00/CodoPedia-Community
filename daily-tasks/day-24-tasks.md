---
description: 'Date : 25 November 2020'
---

# Day 24 : Tasks

## Aptitude 

`Asked in Amazon Online Test`

Sarah, Glen, Rita, Monica, Natalie, and Ana are 6 best friends who had gone out to a party. They were made to sit around a hexagonal table in the restaurant. No two persons out of glen, Ana and Sarah sat opposite to each other. if Ana is sitting between Natalie and Rita, then who are sitting adjacent to Monica? 

* Natalie and Glen
* Sarah and Glen
* Rita and Ana
* Rita and Glen

{% hint style="success" %}
**Ans:** Natalie and Glen
{% endhint %}



## Technical MCQ

**C++:** Friend declaration 

* Must be in the public part
* Must be in the private part
* Can be in protected part but not in the private part
* Can be in public or private part

{% hint style="success" %}

{% endhint %}

## Coding Question

`Asked in Amazon Online Test`

There are n servers numbered from 0 to n-1 connected by undirected server-to-server connections forming a network where **connections\[i\] = \[a, b\]** represents a connection between servers a and b. Any server can reach any other server directly or indirectly through the network.

A critical connection is a connection that, if removed, will make some server unable to reach some other server.

**Return all critical connections in the network in any order.**

**Example 1:**

```text
Input: n = 4
connections = [[0,1],[1,2],[2,0],[1,3]] 

Output: [[1,3]] 
```

**Explanation**: \[\[3,1\]\] is also accepted.

{% hint style="info" %}
**Concept : Articulation Point & bridge**
{% endhint %}

### Solution:

```cpp
vector<pair<int,int>> ans;
int *in, *low, *visited;
vector<int> *adj;
int timer = 1;
void dfs(int node, int parent){
in[node] = low[node] = timer;
visited[node] = 1;
timer++;
for(int child: adj[node])
{
if(child == parent) continue;
if(visited[child] == 1)
low[node] = min(low[node], low[child]);
else{dfs(child, node);
low[node] = min(low[node], low[child]);
if(in[node] < low[child])
{
ans.push_back({node+1, child+1});
}
}
}
}
vector<pair<int,int>> criticalConnections(int n, int edges, vector<pair<int,int>>& connections) {
adj = new vector<int>[n];
for(int i=0; i<connections.size(); i++)
{
int a = connections[i].first-1, b = connections[i].second-1;
adj[a].push_back(b);
adj[b].push_back(a);
}
ans.clear();
in = new int[n];
low = new int[n];
visited = new int[n];
for(int i=0; i<n; i++) visited[i] = 0;
timer = 0;
dfs(0, -1);
return ans;
}
```

### 




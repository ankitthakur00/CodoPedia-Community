---
description: 21-11-2020
---

# Day 20: Tasks

## Aptitude 

The ratio of the number of teachers to the number of students is 1:25. If 36 more students join, the ratio becomes 1:28.the number of teachers in the school is

* 8 
* 12 
* 16 
* 20

{% hint style="success" %}
Ans: 12  
  
let the ratio of students and teachers be x

we have 1/25

now 36 more students joined

x/25×+36=1/28

28×=25×+36

3×=36

×=12
{% endhint %}

## Technical MCQ

A red black tree has the property that there are no 2 reds in a row. Considering you relax it so that there are no 3 reds in a row, calling it relaxed red black trees Which of the following statements regarding the given scenario is false?

1. There is a relaxed red black tree that is not also a red black tree.
2. Every red black tree is also a relaxed red black tree.
3. Every Binary search tree can be turned into a relaxed red black tree.
4. The height of every relaxed red black tree with n node is O\(logn\).

{% hint style="success" %}
**Ans:**  Every Binary search tree can be turned into a relaxed red black tree  
Explanation : [http://andrew-exercise.blogspot.com/2015/11/algorithms-design-and-analysis-part-1\_75.html?m=1](http://andrew-exercise.blogspot.com/2015/11/algorithms-design-and-analysis-part-1_75.html?m=1)
{% endhint %}

## Coding Question

 Given a n x n matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.  
Note that it is the kth smallest element in the sorted order, not the kth distinct element.

**Input :**

```text
 matrix = [
 [ 1, 5, 9],
 [10, 11, 13],
 [12, 13, 15]
],
k = 8
```

**Output :**

```text
13
```

**Solution :**

```cpp
class KthSmallestInSortedMatrix {
 public:
  struct numCompare {
    bool operator()(const pair<int, pair<int, int>> &x, const pair<int, pair<int, int>> &y) {
      return x.first > y.first;
    }
  };

  static int findKthSmallest(vector<vector<int>> &matrix, int k) {
    int n = matrix.size();
    priority_queue<pair<int, pair<int, int>>, vector<pair<int, pair<int, int>>>, numCompare> minHeap;

    // put the 1st element of each row in the min heap
    // we don't need to push more than 'k' elements in the heap
    for (int i = 0; i < n && i < k; i++) {
      minHeap.push(make_pair(matrix[i][0], make_pair(i, 0)));
    }

    // take the smallest element form the min heap, if the running count is equal to k return the number
    // if the row of the top element has more elements, add the next element to the heap
    int numberCount = 0, result = 0;
    while (!minHeap.empty()) {
      auto heapTop = minHeap.top();
      minHeap.pop();
      result = heapTop.first;
      if (++numberCount == k) {
        break;
      }

      heapTop.second.second++;
      if (n > heapTop.second.second) {
        heapTop.first = matrix[heapTop.second.first][heapTop.second.second];
        minHeap.push(heapTop);
      }
    }
    return result;
  }
};

//The space complexity of the above solutions will be O(N) and the time complexity will be O(min(K,N)+K∗logN)
```


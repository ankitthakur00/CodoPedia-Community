---
description: 05-12-2020
---

# Day 5: Tasks

## Aptitude

Five boys were climbing a hill. J was following H. R was just ahead of G. K was between G & H. They were climbing up in a column. Who was the second? Five boys were climbing a hill. J was following H. R was just ahead of G. K was between G & H. They were climbing up in a column. Who was the second?

* R
* G
* K
* H

{% hint style="success" %}
**Ans**  : G  
  
\(B\) implies J &lt; H ........\(i\)  
\(C\) imples R &gt; G .......\(ii\)  
\(D\) implies H &lt; K &lt; G .........\(iii\)  
∴ from \(i\), \(ii\) and \(iii\) J &lt; H &lt; K &lt; G &lt; R i.e. Govind is second 
{% endhint %}

## Technical MCQ

Minimum number of queues needed to implement priority queue?

* **1**
* **2**
* **3**
* **None of these**

{% hint style="success" %}
**Ans :** 2

Priority Queue is an extension of queue[ ](http://quiz.geeksforgeeks.org/queue-set-1introduction-and-array-implementation/)with following properties.  
1\) Every item has a priority associated with it.  
2\) An element with high priority is de-queued before an element with low priority.  
3\) If two elements have the same priority, they are served according to their order in the queue.

* **The minimum number of queues needed in this case is two. One queue is intended for sorting priorities while the other queue is intended for actual storage of data**.
{% endhint %}

## Coding Question

Given an array of integers A. There is a sliding window of size B which is moving from the very left of the array to the very right. You can only see the w numbers in the window. Each time the sliding window moves rightwards by one position. You have to find the maximum for each window.

The array A is \[1 3 -1 -3 5 3 6 7\], and B is 3.

Return an array C, where C\[i\] is the maximum value of from A\[i\] to A\[i+B-1\].

Note: If B &gt; length of the array, return 1 element with the max of the array.

```cpp
Input : A = [1, 3, -1, -3, 5, 3, 6, 7]  , B = 3 
Output : [3, 3, 5, 5, 6, 7]
```

### **Solution :**

{% hint style="success" %}
The double-ended queue is the perfect data structure for this problem. It supports insertion/deletion from the front and back. The trick is to find a way such that the largest element in the window would always appear in the front of the queue. How would you maintain this requirement as you push and pop elements in and out of the queue?

You might notice that there are some redundant elements in the queue that we shouldn’t even consider about. For example, if the current queue has the elements: \[10 5 3\], and a new element in the window has the element 11. Now, we could have emptied the queue without considering elements 10, 5, and 3, and insert only element 11 into the queue.

A natural way most people would think is to try to maintain the queue size the same as the window’s size. Try to break away from this thought and try to think outside of the box. Removing redundant elements and storing only elements that need to be considered in the queue is the key to achieve the efficient O\(n\) solution.
{% endhint %}

```cpp
vector<int> Solution::slidingMaximum(const vector<int> &a, int k) {
        deque<int>s;
        s.push_back(0);
        for(int i=1;i<k;i++)
        {
            while(!s.empty() && a[s.back()]<=a[i])
            s.pop_back();
            s.push_back(i);
        }
        vector<int>v;
        v.push_back(a[s.front()]);
        for(int i=k;i<a.size();i++)
        {
            while(!s.empty() && s.front()<=i-k)
            s.pop_front();
            while(!s.empty() && a[s.back()]<=a[i])
            s.pop_back();
            s.push_back(i);
           v.push_back(a[s.front()]);
        }
    return v;
}
```


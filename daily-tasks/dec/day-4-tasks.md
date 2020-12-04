---
description: 'Date: 04 December 2020'
---

# Day 4 : Tasks

### Aptitude

Find the compound interest on Rs. 10000 for 12 months at 10% per annum. If the interest is compounded half-yearly.

* 260000
* 250000
* 350000
* 360000

{% hint style="success" %}
**Ans :** 260000
{% endhint %}

![](../../.gitbook/assets/capture%20%281%29.png)

## Technical MCQ

What is it called where a child object gets killed if the parent object is killed? 

* Aggregation
* Composition
* Encapsulation
* Association

{% hint style="success" %}
**Ans:** Composition ****

**Explanation:** Composition occurs when a child object gets killed if the parent object gets killed. Aggregation is also known as strong Aggregation.
{% endhint %}

## Coding Question

Given N bags, each bag contains Bi chocolates. There are a kid and a magician. In one unit of time, the kid chooses a random bag I, eats Bi chocolates, then the magician fills the ith bag with floor\(Bi/2\) chocolates.

**Find the maximum number of chocolates that kids can eat in A units of time.**

**`NOTE:`** `floor() function returns the largest integer less than or equal to a given number. Return your answer modulo 10^9+7`

**Example Input :**

**`Input 1:`**

```text
A = 3
B = [6, 5] 
```

**`Input 2:`**

```text
A = 5 
B = [2, 4, 6, 8, 10]
```

**Example Output :**

**`Output 1:`**

```text
14 
```

**`Output 2:`**

```text
33
```

**Example Explanation:**

> `At t = 1 kid eats 6 chocolates from bag 0, and the bag gets filled with 3 chocolates.`
>
> `At t = 2 kid eats 5 chocolates from bag 1, and the bag gets filled by 2 chocolates.` 
>
> `At t = 3 kid eats 3 chocolates from bag 0, and the bag gets filled with 1 chocolate.` 
>
> `so, total number of chocolates eaten are` **`6 + 5 + 3 = 14`**

### **Solution:**

{% hint style="success" %}
Solution for this problem can be found greedily. At any time t, the kid will always choose the bag with the maximum number of chocolates and consume all its chocolates. So we need to maintain the current maximum size among all bags for every time t = 1, …, K and also updating the sizes of the bags.
{% endhint %}

```cpp
long long int mod = 1000000007;
int Solution::nchoc(int A, vector<int> &B) {
	int N = B.size();
	int K = A;
	long long int ans = 0;
	priority_queue<int> heap(B.begin(),B.end());
	while(K--){
		long long int max_elem = heap.top();
		ans += max_elem;
		ans = ans % mod;
		heap.pop();
		heap.push((int)(max_elem/2));
	}   
	return ans;
}
```


---
description: 29-11-2020
---

# Day 28 : Tasks

## Aptitude 

'X' is the wife of 'Y', 'Y' is the brother of 'Z' and 'Z' is the son of 'P'. How is 'P' related to 'X'?

* Sister
* Aunt
* Brother
* Father in Law

{% hint style="success" %}
Ans : Father in Law  
  
Explanation :

### The relationship chart, based on the given problem can be worked out as given below. 'Y' is the brother of 'Z' who is son of "P' So. Z' is  also the son of 'P' When 'P' is the father of 'Y' and X' is the wife of 'Y' then 'P is the father-in-law of 'X'

![solution](https://haygot.s3.amazonaws.com/questions/95047_109066_ans_e484e7c47a454559a65b69638b68a886.png)
{% endhint %}

## **Technical MCQ**

A dedicated path is needed in \_\_\_\_\_\_\_\_ **switching before the data is sent from the sender to the receiver but it is not needed in**    -------- switching.

1. Packet, time division
2. space division, packet
3. packet, circuit
4. circuit, packet

{% hint style="success" %}
Ans : Circuit, Packet
{% endhint %}

## Coding Question

There are **N** number of Pizza bowls and in each bowl there are **a**i pizzas . You can eat pizzas from any bowl but you cannot eat pizzas from two consecutive bowls . Find the maximum number of pizzas you can eat.

**Input:**  
First line of input contains a positive integer **T** denoting number of test cases. For each test case, first line contains N denoting number of pizza bowls . Second line contains N space seperated integers where each of them denotes number of pizzas in ith bowl.

**Output:**  
For each test case print the maximum number of pizzas you can eat.

**Your Task:**  
This is a functional problem you don't need to take input just complete the function **maxPizza\(\)** which accepts two parameters an integer **N** \(number of bowls\) and an array **arr** \(contains number of pizzas in ith bowl\) and returns the maximum number pizzas you can eat.

**Constraints:**  
1 &lt;= T &lt;= 100  
1 &lt;= N &lt;= 105  
1 &lt;= ai &lt;= 109

**Example:**  
**Input:**  
2  
5  
1 2 3 4 5  
5  
5 3 4 11 2  
**Output:**  
9  
16

**Explanation:  
Testcase1:** you can eat pizzas from bowl number 1, 3 and 5.  
**Testcase2:** you can eat pizzas from bowl number 1 and 4.  
 

**Solution :**

```cpp
int maxPizza(int n , int arr[])
{
    vector<int>v(n,0);
    v[0]=arr[0];
    
    if(n==1) return v[0];
    
    v[1]=max(arr[0],arr[1]);
    
    for(int i=2;i<n;i++)
        v[i]=max(v[i-1],arr[i]+v[i-2]);
        
    return v[n-1];
}
```


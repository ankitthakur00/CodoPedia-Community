---
description: 20 December 2020
---

# Day 20 : Tasks

## Aptitude

## A train leaves the station 1 hour before the scheduled time. The driver decreases its speed by 50 km/hr. At the next station 300 km away the train reached on time. Find the original speed of the train.

1. 100
2. 150
3. 125
4. 200

{% hint style="success" %}
**Answer: 150 km/hr**

### Let the normal speed of the train =x km/hr.

### Then the normal time to cover 300 km =300**/x**​.

### Now it takes 1 hour more. So, the new time taken = 1+\(300​/x\)=\(x+300\)/x​.

### ∴ the new speed =300÷\(\(x+300\)/x\)​ km/hr= 300x/\(x+300\)​ km/hr.. But the new speed is \(x=50\) km/hr.

### ⇒300x/\(x+300\)​=x−50

### ⇒x2−50x−15000=0

### ⇒\(x−150\)\(x+100\)=0⇒x=\(150,−100\) km/hr. We reject the negative value as the train always runs in the same direction.

### ∴x=150 So, the normal speed of the train =150 km/hr.
{% endhint %}

## Coding Question

You are given an integer N. You have to count how many possible combinations of numbers from 1 to N \(excluding 1 and N\). which are dividing the number N and after multiplication exactly equal to the value N.

For Example: Let suppose, I have a number 12 and the number that divides 12 between 1 to 12 are 2, 3, 4, 6 we can form N by multiply 2_6, 3_4 and 2_2_3. So, there are 3 possible combinations for number 12. Note: We will not consider 1 and N we will try to find the combinations in between them.

```text
Sample Input:
3
12
8
32

Sample Output:
3
2
6

Explanation:
For test case 1: For value 12 we have 3 combinations in total.
[ [2, 6], [2, 2, 3], [3, 4] ]

For test case 2: For value 8 we have only 2 combinations:
[ [2, 2, 2] , [2, 4] ]
```

## Solution:

```cpp
int getFactors(int n) {
    if(n<=3) return 0;
    vector<int>v;
    for(int i=2;i<=sqrt(n);i++)
    {
        if(n%i==0)
        {v.push_back(i);
        if(n%(n/i)==0 && n/i!=i)
        v.push_back(n/i);
        }
    }
    sort(v.begin(),v.end());
    vector<int>k(n+1,0);
    k[1]=1;
    for(int i=0;i<v.size();i++)
        for(int j=v[i];j<=n;j+=v[i])
            k[j]+=k[j/v[i]];
    return k[n];
}
```


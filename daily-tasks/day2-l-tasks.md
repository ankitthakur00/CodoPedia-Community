---
description: 'Date: 31 October 2020'
---

# Day 2 : Tasks

## Aptitude

Three boys agree to start together and run, until all come together again, round a circular court 15m in circumference. One runs at the rate of 6, the second at 7, and the third at 8km per hour. The race will end after

1. 50 sec 
2. 42 sec 
3. 36 sec 
4. 54 sec

{% hint style="success" %}
Ans: 54 Sec

When three persons A, B and C are running around a circular track of length L meteres with speeds of a, b and c m/s in the same direction direction, They meet each other at any point on the track is {\(L/\(a-b\)\) , \(L/\(b-c\)\) } seconds
{% endhint %}

## Technical MCQ

Tables in second normal form 2NF: 

1.  Eliminate all hidden dependencies 
2.  Eliminate the possibility of insert anomaly 
3. Have a composite key 
4. Have all non-key fields depend on the whole primary key

{% hint style="success" %}
Have all non key fields depend on the whole primary key

**Concept** : DBMS Normalization 
{% endhint %}





## Coding Question

L. Lalit is fond of vehicle numbers. L. Lalit wants to compute the number of vehicles that can be registered in the mirzapur. A vehicle normally has a registration number like **ST 01 AB 1234** . Each registration number has four parts separated by spaces. The first part has two letters common for all cars in the state, The next two digit number is the number of the district where the car is registered within the state. It is always two digits and may have a leading zero. After that, the next part consists of two letters \(AB\), with each letter selected from a range denoting the series and the last part is a 4-digit number . The entire registration number is unique to each vehicle . You have been given the number of districts in the mirzapur and a range of letters and a set of digits that can be used for forming a vehicle registration number. You need to find the maximum number of vehicles that can be registered in the Mirzapur subject to the rules.

**Input :** 

```text
2 A C 1 2
```

**Output :** 

```text
288
```

**Solution:**

```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
long long dist;
cin>>dist; // Number of Districts
char r1,r2;
cin>>r1>>r2; // First and last character of range of letter
int rd1,rd2;
cin>>rd1>>rd2;
// First and last number of the range
int c=int(r2-r1)+1; // Range of letter from r1 to r2
long long int d=rd2-rd1+1; // Range of numbers from rd2 to rd1
long long ans=1ll*dist*pow(c,2)pow(d,4);
//ans = (1*long long )(no. of districts )(range of letter for first position)(range of letter for second position )*(range of numbers for all four positions i.e pow(d,4))
cout<<ans<<endl;
}
```




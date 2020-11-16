---
description: 'Date : 16 November 2020'
---

# Day 15 : Tasks

## Aptitude

The average marks of 48 students in a class are 45. The average marks of the boys in the class is 40 and the average marks of the girls in the class is 50. What is the ratio between the numbers of boys and the number of girls in the class?

2:1   
11:1   
1:1   
1:2

{% hint style="success" %}
Answer : 1:1  
Total marks of 48 students =48x45=2160   
Let the number of boys be B and the number of girls be \(48−B\)   
Then total marks of boys =40B   
Total marks of girls =50\(48−B\)=2400−50B ⇒ 40B+2400−50B=2160 ⇒ 10B=240 ⇒ B=24   
Thus number of girls =48−24=24   
Therefore, required ratio =24:24=1:1
{% endhint %}

## Technical

class technical{  
 public static void main\(String\[\] as\) {   
long l=2147483649;  
System.out.println\(l\);   
}   
}

1. Compilation Error
2. Runtime Error
3. Garbage Value
4. 2147483649

{% hint style="success" %}
Answer: Compilation Error  


```text
Main.java:12: error: integer number too large
		  long l=2147483649;
```
{% endhint %}

## Coding Question

Given two integers n and k, Find the lexicographical nth palindrome of k digits.

```text
Input : 
n = 5, k = 4 
Output: 1441
Explanation: 
4 digit lexicographical palindromes are: 1001, 1111, 1221, 1331, 1441 
5th palindrome = 1441
```

### Solution\(In C++\)

```cpp
void nthPalindrome(int n, int k) 
{ 
    // Determine the first half digits 
    int temp = (k & 1) ? (k / 2) : (k/2 - 1); 
    int palindrome = (int)pow(10, temp); 
    palindrome += n - 1; 
  
    // Print the first half digits of palindrome 
    cout<< palindrome; 
  
    // If k is odd, truncate the last digit 
    if (k & 1) 
        palindrome /= 10; 
  
    // print the last half digits of palindrome 
    while (palindrome) 
    { 
        cout<< palindrome % 10; 
        palindrome /= 10; 
    }   
   cout<<”\n”;
}
```


---
description: 'Date : 3 November 2020'
---

# Day 5: Tasks

## Aptitude

A cube of edge 6 cm is painted on all sides and then cut into unit cubes. What is the number of unit cubes with only one side painted?

84  
96  
104   
None of the above

{% hint style="success" %}
96  
Shortcut Formulas :

For a cube of side n\*n\*n painted on all sides which is uniformly cut into smaller cubes of dimension 1\*1\*1,

Number of cubes with 0 side painted= \(n-2\)³

Number of cubes with 1 side painted =6\(n - 2\)²

umber of cubes with 2 sides painted= 12\(n-2\)

Number of cubes with 3 sides painted= 8\(always\)  
{% endhint %}

## Technical

Consider an AVL tree constructed from the given below nodes :   
7, 6, 8, 5, 3, 2, 4, 1  
Let this AVL tree be stored in an array A, then what will be the value of A\[4\]?  
Note: Array Index starts from 1  


{% hint style="success" %}
Answer = 2  
  
In array, we always store level order traversal  
so, the array would be  
\[ 5 3 7 2 4 6 8 1\]
{% endhint %}

![AVL Tree for given array](../.gitbook/assets/untitled-diagram%20%281%29.png)

## Coding 

At a lemonade stand, each lemonade costs $5. 

Customers are standing in a queue to buy from you, and order one at a time \(in the order specified by bills\).

Each customer will only buy one lemonade and pay with either a $5, $10, or $20 bill.  You must provide the correct change to each customer so that the net transaction is that the customer pays $5.

 Note that you don't have any change in hand at first.

 Return true if and only if you can provide every customer with correct change.

#### Example

```text
Input: [5,5,5,10,20]
Output: true
Explanation: 
From the first 3 customers, we collect three $5 bills in order.
From the fourth customer, we collect a $10 bill and give back a $5.
From the fifth customer, we give a $10 bill and a $5 bill.
Since all customers got correct change, we output true.
```

#### Solution\(Java\)

```java
public boolean lemonadeChange(int[] bills) {
        int five = 0, ten = 0;
        for (int bill: bills) {
            if (bill == 5)
                five++;
            else if (bill == 10) {
                if (five == 0) return false;
                five--;
                ten++;
            } 
            else {
                if (five > 0 && ten > 0) {
                    five--;
                    ten--;
                } 
                else if (five >= 3) {
                    five -= 3;
                } 
                else {
                    return false;
                }
            }
        }

        return true;
    }
```

### 


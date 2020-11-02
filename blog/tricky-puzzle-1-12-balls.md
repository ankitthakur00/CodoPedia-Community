---
description: 'Asked in Google, Facebook, Amazon, Udaan, Nautanix, Netflix'
---

# Tricky Puzzle - 1\(12 Balls\)

## Problem Statment

You have 12 balls identical in every way except that one of them weighs slightly less or more. You have a balance scale. Find the Minimum number of comparisons to find the defected ball.

{% hint style="success" %}
Answer - 3
{% endhint %}

## Explanation

Let us number our balls from 1 to 12, so we have {1,2,3,4,5,6,7,8,9,10,11,12}. Divide these balls into three Groups:  
G1 = {1,2,3,4}  
G2 = {5,6,7,8}  
G3 = {9,10,11,12}  
**Weigh G1 and G2,**  
_Now Three cases rise,_

{% tabs %}
{% tab title="weight\(G1\) = weight\(G2\) " %}
**This means the defected ball is in G3**

So, suspected balls are {9,10,11,12} and confirmed balls are {1,2,3,4,5,6,7,8}.

Now make two more groups named,  
G4 = {8,9} and G5 = {10,11}  
Note: Ball no. 8 is not defected one.  
Now weigh G4 and G5 and three cases rise,

**a\) weight\(G4\) = weight\(G5\)**  
Our answer is ball 12.  
  
**b\) weight\(G4\) &gt; weight\(G5\)**  
Either {9} is heavy or {10,11} is light, so weigh {10} and {11}  
                          _if both are equal then, ans={9}, else ball with less weight will be answer._  
  
**c\) weight\(G4\) &lt; weight\(G5\)**  
Either {9} is light or {10,11} is heavy, so weigh {10} and {11}  
                          _if both are equal then, ans={9}, else ball with heavy weight will be answer._  
  
**The Maximum comparison in each case for this scenario is 3.**
{% endtab %}

{% tab title="weight\(G1\) > weight\(G2\) " %}
**This means either G1 is heavier or G2 is lighter.**   
So, Suspected balls are {1,2,3,4} and {5,6,7,8} and confirmed balls are {9,10,11,12}  
  
Now make two groups,  
G8 = {1,2,5} and G9 = {3,6,9}  
Now weigh them and three cases arise :  
  
**a\) weight\(G8\) = weight\(G9\)**  
So, now suspects balls are {4,7,8} and rest are confirmed balls.  
Since weight\(G1\)&gt; weight\(G2\) so, either {4} is heavy or either of {7,8} is light.  
_Weight ball {7} and ball {8} , if equal answer is ball {4} else answer is ball with lighter weight._  
  
**b\) weight\(G8\) &gt; weight\(G9\)  
S**o either of {1,2,5} is heavy or {3,6} is lighter.  
_**Point to think here: Ball {5} and {3} are no more suspected because, if {5} was heavy then, weight\(G2\) would have been greater and similarly if {3} has been lighter then also weight\(G2\) would have been greater.**_  
****So now we can say either of {1,2} is heavy or {3} is lighter.  
W_eigh ball {1} and ball {2} , if equal answer is ball {3} else answer is ball with heavier weight._  
  
**c\) weight\(G8\) &lt; weight\(G9\)**   
So either of {1 , 2 , 5 } is light or {3 , 6 } is heavier.  
_**Point to think here: Ball {1,2 } can not be light since the weight of G1 is more and also ball {6} can not be heavy as the weight of G2 is less.**_  
****So either {5} is lighter or {3} is heavier.   
W_eigh ball {5} with ball {9} , if equal  answer is ball {3} else answer is ball {5}._  
  
**The Maximum comparison in each case for this scenario is 3.**
{% endtab %}

{% tab title="weight\(G1\) < weight\(G2\) " %}
**This means either G1 is lighter or G2 is heavier.**   
So, Suspected balls are {1,2,3,4} and {5,6,7,8} and confirmed balls are {9,10,11,12}

Now make two groups,  
G10 = {1, 5 , 6 } and G11 = {2 , 7 , 9}  
Now weigh them and three cases rise :  
  
**a\) weight\(G10\) = weight\(G11\)**  
So, now suspects balls are {3 ,4,8} and rest are confirmed balls.  
Since weight\(G1\)&lt;weight\(G2\) so, either {3 ,4} is lighter or either of {8} is heavy.  
_Weigh ball {3} and ball {4} , if equal answer is ball {8} else answer is ball with lighter weight._  
  
**b\) weight\(G10\) &gt; weight\(G11\)**  
So either of {1 , 5 , 6 } is heavy or {2,7} is lighter.  
_**Point to think here: Ball {1} and {7} are no more suspected because, if {1} was heavy then,   weight\(G2\) would have been lesser and similarly if {7} has been lighter then also weight\(G2\) would have been lesser.**_  
****So now we can say either of {5,6} is heavy or {2} is lighter.  
_Weigh ball {5} and ball {6}, if equal answer is ball {2} else answer is a ball with heavier weight._  
  
c **\) weight\(G10\) &lt; weight\(G11\)**  
So either of {1 , 5 , 6 } is lighter or {2,7} is heavier.  
_**Point to think here: Ball {5} and {6} are no more suspected because, if they would have been lighter then weight\(G2\) would have been less. Similarly, ball {2} is not heavier, as weight\(G2\) is more.**_  
****So now we can say either {1} is lighter or {7} is heavier.  
_Weigh ball {1} and ball {9} if equal answer is ball {7} else answer is a ball with heavier weight._

**The Maximum comparison in each case for this scenario is 3.**
{% endtab %}
{% endtabs %}



### Author's Note

"The solution is tricky so read it at least thrice to grasp the concept thoroughly."






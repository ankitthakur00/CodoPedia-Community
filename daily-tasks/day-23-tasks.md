---
description: 24th November 2020
---

# Day 23 : Tasks

## Aptitude

If in a certain language, GAMBLE is coded as FBLCKF, how is FLOWER coded in that code?

1. GKPVFQ
2. EMNXDS
3. GMPVDS
4. HNQYGT
5. EKNVDQ

{% hint style="success" %}
Answer: EMNXDS

The first , third and fifth letters are each moved one step backward, while the second, fourth and sixth letters are each moved one step forward to obtain the corresponding letters of the code.
{% endhint %}

## Technical Question

```cpp
Given a piece of code, Identify the given statements:

class temp
{
  private: int x;
  public: int getx();
          int gety();

  private: int y;

  public: int printx(int);
}

```

1. Access specifier can be defined as many time in a class as you require.
2. Access specifier can be defined as many time in the case of public only.
3. Once one access specifier is defined it cannot be defined in the same class.
4. Access specifier can be defined only once if it is a base class, if the class is a derived class then it can have as many times it requires.

{% hint style="success" %}
Answer: Access specifier can be defined as many time in a class as you require.
{% endhint %}

## Coding Question

Given two non-empty binary trees s and t, check whether tree t has exactly the same structure and node values with a subtree of s. A subtree of s is a tree consists of a node in s and all of this node's descendants. The tree s could also be considered as a subtree of itself.

```cpp
bool check(vector<int> &parent,vector<int> &child)
{
    string s1="";
    string s2="";
    
    for(int i=0;i<parent.size();i++)
    s1+=to_string(parent[i]);
    
    for(int i=0;i<child.size();i++)
    s2+=to_string(child[i]);
    
    if(s1.find(s2)!=-1)
    return true;
    return false;
}
void inorder(tnode *root,vector<int> &v)
{
    if(!root)
    {
        v.push_back(-1);
        return;
    }
    
    inorder(root->left,v);
    v.push_back(root->value);
    inorder(root->right,v);
}
void preorder(tnode *root,vector<int> &v)
{
    if(!root)
    {
        v.push_back(-1);
        return;
    }
    v.push_back(root->value);
    preorder(root->left,v);
    preorder(root->right,v);
}
bool isSubtree(tnode  *root1,tnode *root2)
{
    
    vector<int> in1;
    vector<int> in2;
    vector<int> pre1;
    vector<int> pre2;
    
    inorder(root1,in1);
    inorder(root2,in2);
    preorder(root1,pre1);
    preorder(root2,pre2);
    
    if(check(in1,in2)&&check(pre1,pre2))
    return true;
    return false;
    
}
```


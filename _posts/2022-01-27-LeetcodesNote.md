---
layout: post
read_time: true
show_time: ture
title: "LeetCode刷题笔记"
img: posts/20220127/leetcode.png
tags: [Note,LeetCode]
category: Code
author: Wsx
description: "Leetcode"
---

## leetcode刷题
## 目录
 - [28. 对称的二叉树](#对称的二叉树)
## 对称的二叉树
### 请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。
例如，二叉树 [1,2,2,3,4,4,3] 是对称的。 

> 解题思路: \
> 递归判断,根据对称判断root的left==right，在判断left->left==right->right && left->right==right->left

##### 算法流程
**isSymmetric**:
- 特例处理:若根节点root为空,返回true.
- 返回值: compare(root.left,root.right);

**compare(left,right)**:
- 条件处理  
  1.若left==NULL,right==NULL返回true   
  2.当只有left，right中的一个为NULL,返回false; 
  
- 返回值:返回compare(left.left,right.right)&&compare(left.right,right.left)

{%highlight c %}
bool compare(struct TreeNode*left,struct TreeNode*right)
{
    if((!left&&right) ||(left&&!right))
        return false;
    if(!left&&!right)
        return true;
    // else
    //     return false;
    // if(left->val != right->val)
    //     return false;
    return (left->val==right->val) && compare(left->left, right->right) && compare(left->right,right->left);
}

bool isSymmetric(struct TreeNode* root){
    if(!root)
        return true;
    return compare(root->left,root->right);
} 
{% endhighlight %}
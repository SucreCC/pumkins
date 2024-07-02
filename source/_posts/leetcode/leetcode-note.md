---
title: Leetcode notes
sticky: true
date: 2024-6-29 10:16:00
layout: categories
categories:
- [Blog]
tags:
- Sucre
- Leetcode
- notebook
- Java
---

Notes for leetcode


<!-- more -->

## Arrays
### String

```` Java

String s = "abcde";
List<Character> sl = s.chars().mapToObj(c -> (char) c)
  .collect(Collectors.toList());
````



## Tree

### Maximum deep of tree

```` Java

class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null){
            return 0;
        }

        int left = maxDepth(root.left);
        int right = maxDepth(root.right);

        return (left>right? left : right) + 1;
    }
}
````


### Diameter of tree

```` Java

class Solution {

    int d = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        longestLength(root);
        return d;
    }

    private int longestLength(TreeNode node){

        if(node == null){
            return 0;
        }

        int left = longestLength(node.left);
        int right = longestLength(node.right);

        d = d > left+right? d : left + right;
        return (left>right? left:right) + 1;
    }
}
````




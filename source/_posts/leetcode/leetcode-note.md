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

# Arrays
## String to list

```` Java

String s = "abcde";
List<Character> sl = s.chars().mapToObj(c -> (char) c)
  .collect(Collectors.toList());

````

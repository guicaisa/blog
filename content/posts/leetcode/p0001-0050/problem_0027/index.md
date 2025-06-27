---
title: leetcode 27.移除元素
subtitle:
date: 2025-06-27T23:42:08+08:00
slug: 5bbd7e1
draft: false
author:
  name: Ciao
  link:
  email:
  avatar:
description:
keywords:
license:
comment: false
weight: 0
tags:
  - leetcode
  - algorithm
categories:
  - leetcode
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRelated: false
hiddenFromFeed: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

<!--more-->

<h1 align="center">leetcode 27.移除元素</h1>

### 题目地址
  * https://leetcode.cn/problems/remove-element/

### 解法
  1. 双指针
  * 使用一个单独的指针指向数组头部，然后用另外一个指针遍历数组，遇到与val不同的值则根据第一个指针赋值到数组中，并指向下一个位置，否则就略过，数组遍历结束后，前n个元素即所有不等于value的元素
    ```C++
    int removeElement(vector<int>& nums, int val) 
    {
      int n = 0;
      for (int i = 0; i < nums.size(); ++i)
      {
          if (nums[i] != val)
          {
              nums[n++] = nums[i];
          }
      }
      return n;
    }
    ```

  2. 反向指针
  * 双指针的另一种处理方式，跟方法一差不多，不过第二个指针指向了尾部，在遍历数组的过程中将与val相同的元素与尾部元素互换，并且将尾部指针往前挪，数组遍历只能遍历到尾指针之前，因为尾指针之后存储的都是需要排除的元素
    ```C++
    int removeElementTailPointer(vector<int>& nums, int val)
    {
        int tail = nums.size();
        for (int i = 0; i < tail; )
        {
            if (nums[i] == val)
            {
                nums[i] = nums[--tail];
            }
            else
            {
                ++i;
            }
        }
        return tail;
    }
    ```
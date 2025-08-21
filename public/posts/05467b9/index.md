# Leetcode 11.盛最多水的容器


<!--more-->

<h1 align="center">leetcode 11.盛最多水的容器</h1>

### 题目地址
  * https://leetcode.cn/problems/container-with-most-water/

### 解法
  1. 双指针
  * 左右指针相向遍历，计算每次的面积，每次遍历时移动短边，在宽度变小的情况下，提高高度才能获得更大的结果
    ```C++
    int maxArea(vector<int>& height) 
    {
        int max_area = 0;
        int left = 0;
        int right = height.size() - 1;
        while (left <= right)
        {
            int h = min(height[left], height[right]);
            int w = right - left;
            max_area = max(max_area, h * w);
            if (height[left] < height[right])
            {
                ++left;
            }
            else
            {
                --right;
            }
        }

        return max_area;
    }
    ```


---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/05467b9/  


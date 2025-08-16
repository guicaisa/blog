# Leetcode 167.两数之和 II - 输入有序数组


<!--more-->

<h1 align="center">leetcode 167.两数之和 II - 输入有序数组</h1>

### 题目地址
  * https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/
  
### 解法
  1. 双指针
  * 左右指针相向遍历，相加之后与target判断大小，如果相等就直接返回答案，由于数组是升序排列的，根据相加的值与target大小的判断，来定义下次的遍历方向，比target小，需要更大和，所以左边的指针右移，反之亦然
    ```C++
    vector<int> twoSum(vector<int>& numbers, int target) 
    {
        int left = 0;
        int right = numbers.size() - 1;
        while (left < right)
        {
            int sum = numbers[left] + numbers[right];
            if (sum == target)
            {
                return vector<int>{left+1, right+1};
            }
            if (sum < target)
            {
                ++left;
            }
            else
            {
                --right;
            }
        }

        return vector<int>{left, right};
    }
    ```


---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/c779e4e/  


# Leetcode 169.多数元素


<!--more-->

<h1 align="center">leetcode 169.多数元素</h1>

### 题目地址
  * https://leetcode.cn/problems/majority-element/

### 解法
  1. 哈希表
  * 第一时间想到的最简单的方法，使用哈希表存储每个数字出现的次数，通过比较获取出现次数最多的数字
    ```C++
    int majorityElement(vector<int>& nums) 
    {
        unordered_map<int, int> num_count(nums.size());
        int max_count = 0;
        int max_num = 0;
        for (int i = 0; i < nums.size(); ++i)
        {
            int num = nums[i];
            int count = ++num_count[num];
            if (count > max_count)
            {
                max_count = count;
                max_num = num; 
            }
        }   

        return max_num;
    }
    ```

  2. 排序
  * 由于题目描述里已经说明了多数元素的数量大于数组长度的一半，则排序之后该多数元素必然会出现在数组的中间位置上，相较于解法1来说，省略了额外的内存空间 
    ```C++
    int majorityElementSort(vector<int>& nums) 
    {
        if (nums.size() == 0)
        {
            return 0;
        }
        sort(nums.begin(), nums.end());
        return nums[nums.size() / 2];
    }
    ```



---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/71edff3/  


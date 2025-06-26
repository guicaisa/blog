# Leetcode 88.合并两个有序数组


<!--more-->

<h1 align="center">leetcode 88.合并两个有序数组</h1>

### 题目地址
  * https://leetcode.cn/problems/merge-sorted-array/
  
### 解法
  1. 归并排序
  * 题目中的两个数组是有序的，第一时间想到的解决方法就是归并排序，使用两个指针分别指向两个数组的头部进行遍历，比较两个数组中当前指针位置元素的大小，将较小者放入结果数组中，并且将较小元素所在数组的指针指向下一个位置，同时结果数组的指针也指向下一个赋值的位置。结果数组的长度等于两个数组的长度之和，结果数组遍历完之后即全部结束。
  * 这里会使用一个临时数组来作为数组1的拷贝，而数组1本身则作为结果数组，用于存储结果。
    ```C++
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) 
    {
        vector<int> temp_nums = nums1;
        int t = 0;
        int j = 0;
        for (int i = 0; i < nums1.size(); ++i)
        {
            //temp_nums已遍历结束，直接将nums2中的元素放入结果数组中
            //temp_nums由nums1复制得来，只有前m个元素才是有效元素
            if (t >= m)
            {
                nums1[i] = nums2[j++];
                continue;
            }
            //nums2已遍历结束，直接将temp_nums中的元素放入结果数组中
            if (j >= nums2.size())
            {
                nums1[i] = temp_nums[t++];
                continue;
            }
            //否则比较大小，将较小的元素放入结果数组中
            nums1[i] = nums2[j] < temp_nums[t] ? nums2[j++] : temp_nums[t++];
        }
    }
    ``` 
  
  2. 反向双指针
  * 解法1的时间复杂度已经足够小，美中不足的地方在于使用了额外的数组内存，有没有"in-place"的方案呢？
  * 那肯定是有的。不使用额外的数组变量来辅助处理，将双指针指向2个数组的尾部，注意由于数组1中的有效数字只有前m个，所以数字1的指针指向第m个元素即可，无需指向数组1的尾部，两个数组从指定好的位置反向遍历，将较大者放入数组1的尾部，并且将较大元素所在数组的指针指向前一个位置，同时数组1的尾部指针也指向前一个位置。
  * 直接将数组1本身作为结果数组，并且从尾部开始设置元素，由于数组1的后n个元素为无意义的值，并且数组2的长度是n，所以无论数组1和数组2的元素以任何一种方式交叉放入数组1的尾部，都不会导致有效的元素被覆盖掉。
    ```C++
    void mergeReverseTowPointers(vector<int>& nums1, int m, vector<int>& nums2, int n)
    {
        int i = m - 1; //nums1从前m个元素开始
        int j = n - 1;
        for (int index = nums1.size() - 1; index >= 0; --index)
        {
            //nums1已遍历结束，直接将nums2的元素放入结果数组中
            if (i < 0)
            {
                nums1[index] = nums2[j--];
                continue;
            }
            //nums2已遍历结束，直接将nums1的元素放入结果数组中
            if (j < 0)
            {
                nums1[index] = nums1[i--];
                continue;
            }
            //否则比较大小，将较大的元素放入结果数组中
            nums1[index] = nums1[i] > nums2[j] ? nums1[i--] : nums2[j--];
        }
    }
    ```



---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/42f93e1/  


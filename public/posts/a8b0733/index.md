# Leetcode 58.最后一个单词的长度


<!--more-->

<h1 align="center">leetcode 58.最后一个单词的长度</h1>

### 题目地址
  * https://leetcode.cn/problems/length-of-last-word/

### 解法
  1. 遍历
  * 非空格字符时，累加字符串长度，遇到空格时记录长度即可
    ```C++
    int lengthOfLastWord(string s) 
    {
        int len = 0;
        int temp = 0;
        for (int i = 0; i < s.size(); ++i)
        {
            if (s[i] == ' ')
            {
                if (temp != 0)
                {
                    len = temp;
                }
                temp = 0;
            }
            else
            {
                ++temp;
            }
        }

        if (temp != 0)
        {
            len = temp;
        }

        return len;
    }
    ```

---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/a8b0733/  


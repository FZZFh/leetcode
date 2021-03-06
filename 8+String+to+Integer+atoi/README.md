# 题目链接： https://leetcode.com/problems/string-to-integer-atoi/description/

# 1. 算法
atoi常考的面试题，重点考察的就是各种异常情况的处理。


# 2. Python语法
看了论坛里的各种写法，有几点是我代码里可以更加优雅的：
1. 最后判断是否有超出int限制，这么写明显比我的两个if更优雅： ```max(-2**31, min(num ,2**31-1))```
2. 我的代码里用了python两个内建函数，```isdigit()```和```isalpha()```, 这个应该不是所有人都知道。
3. python如果用正则来实现这个会很简单，但相信面试如果考这题，应该不是让写正则，下面是正则写法的代码：
```
import re
pattern = r"^([+-]?\d+).*$"
regex = re.compile(pattern)

class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        i = 0
        int_max =  2 ** 31 - 1
        int_min = -2 ** 31
        s = str.lstrip(" ")
        match = regex.match(s)

        if match:
            i = int(match.group(1))
        if i < 0:
            i = max(i, int_min)
        elif i > 0:
            i = min(i, int_max)
        else:
            pass

        return i
```

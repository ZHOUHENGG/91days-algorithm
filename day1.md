<!--
 * @Author: your name
 * @Date: 2020-06-02 17:11:55
 * @LastEditTime: 2020-06-02 21:44:51
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day1.md
--> 

# 66.加一

## 题目链接

<https://leetcode-cn.com/problems/plus-one>

## 我的回答

```js
var plusOne = function(digits) {
    let len = digits.length-1
    for(let i=len; i>=0; i--) {
      if(digits[i]+1 === 10) {
        digits[i] = 0
      }else {
        digits[i] = digits[i]+1
        return digits
      }
}
  digits.unshift(1)
  return digits
}

```

## 思路

一共有三种情况
1.当个位数加一不等于10时，直接返回数组
2.当个位数加一等于10时，前面一位数加一，返回数组
3.当所有数是9时，所有数为0，在数组首位添加一个1，返回数组

时间复杂度O(n)

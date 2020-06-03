<!--
 * @Author: your name
 * @Date: 2020-06-03 00:14:24
 * @LastEditTime: 2020-06-03 21:44:50
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day3.md
--> 

# 1381. 设计一个支持增量操作的栈

## 题目链接

<https://leetcode-cn.com/problems/design-a-stack-with-increment-operation/>

## 我的回答

```js
/**
 * @param {number} maxSize
 */
var CustomStack = function(maxSize) {
    this.arr = []
    this.maxSize = maxSize
};

/** 
 * @param {number} x
 * @return {void}
 */
CustomStack.prototype.push = function(x) {
    if(this.arr.length < this.maxSize) {
        this.arr.push(x)
    }
}; 

/**
 * @return {number}
 */
CustomStack.prototype.pop = function() {
    if(this.arr.length === 0) {
        return -1
    }
    return this.arr.pop()
};

/** 
 * @param {number} k 
 * @param {number} val
 * @return {void}
 */
CustomStack.prototype.increment = function(k, val) {
    const min = Math.min(k, this.arr.length)
    for(let i= 0; i<min; i++) {
        this.arr[i] = this.arr[i] +val
    }
};

/**
 * Your CustomStack object will be instantiated and called as such:
 * var obj = new CustomStack(maxSize)
 * obj.push(x)
 * var param_2 = obj.pop()
 * obj.increment(k,val)
 */
```

## 思路

使用数组来模拟栈，可以实现时间复杂度 O(1) 的 push 和 pop，和 O(k) 的 inc

满足对象变成私有性的原则可使用ES6的symbol基本数据类型

```js
const _arr = Symbol()
```

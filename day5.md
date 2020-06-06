<!--
 * @Author: your name
 * @Date: 2020-06-04 21:47:25
 * @LastEditTime: 2020-06-06 19:46:05
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day5.md
--> 

## 232. 用栈实现队列

## 题目链接

<https://leetcode-cn.com/problems/implement-queue-using-stacks/>

## 我的回答

```js
let star  = []       //第一个栈
let wars  = []       //第二个栈,辅助栈
let push = x => {
    let cur = null   //中转变量, 每有新的值传进来时清空
    while((cur = star.pop())) {  //当第二个值传进来时,把上一个值从第一个栈推出放入cur
        wars.push(cur)      //把上一个值推入辅助栈
    }
    wars.push(x)    //先给辅助栈推入函数传递的值
    while((cur = wars.pop())) {  //把值从辅助栈最后一个推出,放入中转站
        star.push(cur)      //把cur推入第一个栈
    }
}
console.log(push(1));
console.log(push(2));
console.log(push(3));
console.log(star);
```

<!--
 * @Author: your name
 * @Date: 2020-06-07 15:41:48
 * @LastEditTime: 2020-06-07 23:12:18
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day7.md
--> 


## 206. 反转链表

<https://leetcode-cn.com/problems/reverse-linked-list/>

## 我的回答

```js
var reverseList = function(head) {
    let curr = head;        //表示头节点的指针
    let prev = null;        //跟在头节点之后的指针,作为新的head.next
    while(curr){
        let save = curr.next;   //储存原来的head.next
        curr.next = prev;       //把原来head.next指向prev
        prev = curr;            //prev指针推进到以前的头节点
        curr = save;            //头节点推进
    }
    return prev;
};

var reverseList = function(head) {
    if(!head || !head.next) {     //如果只有一个节点或者到尾节点时返回head
        return head
    }
    let save = head.next           //存储原来的head.next
    let reHead = reverseList(save) //把以前的head.next作为参数传入递归函数
    head.next = null               //断开以前的head.next
    save.next = head               //后一个节点指向head,反转
    return reHead
};


```
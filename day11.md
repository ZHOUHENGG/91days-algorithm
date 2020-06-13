<!--
 * @Author: your name
 * @Date: 2020-06-10 22:46:02
 * @LastEditTime: 2020-06-11 22:03:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day11.md
-->

## 142.环形链表 II

<https://leetcode-cn.com/problems/linked-list-cycle-ii/submissions/>

## 我的回答

1. has法
建立一个Set集合, 遍历整个节点, 把每个节点都添加到Set
如果当前节点不存在,则继续遍历
如果当前节点存在,那么返回该节点

时间复杂度O(n),空间复杂度O(n)

```js
function hasFun(head) {
    let data = new Set()
    while(head) {
        if(data.has(head)) {
            return head
        }else {
            data.add(head)
        }
        head = head.next
    }
    return null
}
```

2.快慢指针
定义一个fast指针,每次前进两步.定义一个slow指针,且每次前进一步
当两个指针相遇时,将fast指针指向链表头部,同时fast每次只前进一步,slow指针继续每次前进一步,再次相遇时就是入口

时间复杂度O(n),空间复杂度O(1)

```js
function myfun() {
    if(head == null && head.next == null) {
        return null
    }
    let fast = head     //快指针
    let slow = head     //慢指针
    // do {
    //     if(fast != null && fast.next != null) {
    //         fast = fast.next.next
    //     }else {
    //         fast = null
    //     }
    //     slow = slow.next
    // }while (fast != slow)

    // if(fast === null ) {
    //     return null
    // }
    // fast = head
    // while (fast != slow) {
    //     fast = fast.next
    //     slow = slow.next
    // }
    // return fast

    while(fast && fast.next) {
        fast = fast.next.next
        slow = slow.next
        if(fast === slow) {
            fast = head
            while(fast != slow) {
                fast = fast.next
                slow = slow.next
            }
            return fast
        }
    }
    return null
}
```

> ## 方法3

> 先用快慢指针确定链表有环，这里就不多说了，快慢指针相遇时，一定是在环内的某个节点。
>
> ![first_node_of_loop_in_linked_list_0](https://user-images.githubusercontent.com/30331289/84380430-e7b85a80-ac19-11ea-9ab3-b7a6f10645fe.png)
>
> 我们分别来看一下两个指针相遇前分别走了多少路程。
>
> **快指针**
> 
> 假设走到相遇点之前，快指针在环内走了 x 圈，那快指针走过的总路程可以用 `S(fast) = a + x(b + c) + b` 来表示，其中 `(b + c)` 就是环的长度。
> 
> ![first_node_of_loop_in_linked_list_1](https://user-images.githubusercontent.com/30331289/84380437-ed15a500-ac19-11ea-9a2c-9ce5b0f3e992.png)
> 
> **慢指针**
> 
> 假设走到相遇点之前，慢指针在环内走了 y 圈，同理可得慢指针走过的总路程是 `S(slow) = a + y(b + c) + b`。
> 
> 而由于快指针的速度是慢指针速度的 2 倍，所以可得以下方程式：
> 
> `S(slow) = 2S(fast)` => `a + x(b + c) + b = 2(a + y(b + c) + b)`
> 
> 稍微整理一下我们就得到了：
> 
> `a + b = (b + c)(x - 2y)`
> 
> 如果我们把其中一个指针移动到链表头部，然后让两个指针以相同的速度移动。
> 
> ![first_node_of_loop_in_linked_list_2](https://user-images.githubusercontent.com/30331289/84380452-f141c280-ac19-11ea-8074-0b2cb71e104c.png)
> 
> 它们会在环的入口相遇。
> 
> ![first_node_of_loop_in_linked_list_3](https://user-images.githubusercontent.com/30331289/84380467-f6067680-ac19-11ea-992a-d3b0b504d3e2.png)
> 
> * 时间复杂度：O(n)
> * 空间复杂度：O(1)

<!--
 * @Author: your name
 * @Date: 2020-06-03 21:48:22
 * @LastEditTime: 2020-06-04 21:38:32
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day4.md
--> 


## 394. 字符串解码

## 题目链接

<https://leetcode-cn.com/problems/decode-string/submissions/>

## 我的回答

<https://github.com/leetcode-pp/91alg-1/issues/20#issuecomment-638623652>

```js
let decodeString = s => {
    let Stack = [];           //创建一个数组模拟栈
    let string = "";          //要拼接的字符串存放处
    let num = 0;              //重复的次数存放处,repeat()方法的参数
    for (const i of s) {      //遍历整个字符串
      if (i >= 0) {
  num += i;             //把i加给num
      } else if (i === "[") { 
        Stack.push(num);      //把num推入栈
        Stack.push(string);   //把已经repeat后的string推入栈(第一次为空)
        string = "";    //string清空(之前string的值已经保存在栈中,会被推出栈赋值给z1)
        num = 0;     //num清零(之前num的值已经保存在栈中,会被推出栈赋值给z2)
      } else if (i === "]") { 
        let z1 = Stack.pop(); //栈推出的第一个值,拼接的字符串
        let z2 = Stack.pop(); //栈推出的第二个值,次数num
        string = z1 + string.repeat(z2);    //给string重新赋值,第一个要拼接的字符串(第一次为空)+第二个要拼接的字符串repeat后的值
      } else {
        string += i;          //如果i是字母时,把i加给string
      }
    }
    return string;
  };
```


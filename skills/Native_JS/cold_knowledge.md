# JavaScript 奇怪又实用的姿势

## 解构小技巧

平常我们需要用到一个嵌套多层的对象中某些属性，会将其解构出来使用

```js
let obj = {
  part1: {
    name: '零一',
    age: 23
  }
}

// 解构
const { part1: { name, age } } = obj
// 使用
console.log(name, age)  // 零一  23
```

这种情况下，你把 `name` 和 `age` 从 `part1` 里解构出来了以后，你就无法使用变量 `obj` 中的 `part1` 属性了，如：

```js
// .... 省略

const { part1: { name, age } } = obj
console.log(part1)   // Uncaught ReferenceError: part1 is not defined
```

其实你可以多次解构，如：

```js
// .... 省略

const { part1, part1: { name, age } } = obj
console.log(part1)   // {name: "零一", age: 23}
```

## 数字分隔符

有时你会在文件中定义一个数字常量

```js
const myMoney = 1000000000000
```

这么多个 `0` ，1、2 ... 6、7 ... 数晕了都，怎么办？

**数字分隔符整起来！**

```js
const myMoney = 1_000_000_000_000

console.log(myMoney)  // 1000000000000
```

这样写是没问题的，而且数字分割开后也更直观！！

## try...catch...finally 谁厉害？

普通函数调用中，`return` 一般会提前结束函数的执行

```js
function demo () {
  return 1
  console.log('我是零一')
  return 2
}

console.log(demo())   // 1
```

而在  `try...catch...finally` 中，`return` 就不会提前结束执行

```js
function demo () {
  try {
    return 1
  } catch (err) {
    console.log(err)
    return 2
  } finally {
    return 3
  }
}

console.log(demo())   // 返回什么？？
```

答案是：`3`

最后得出结论，还是 `finally` 比较厉害

## 一行代码生成随机字符串

 一行超短代码 即可实现 "随机生成字符串" 的功能

```js
const str = Math.random().toString(36).substr(2, 10);
console.log(str);   // 'w5jetivt7e'
```

先是 `Math.random()` 生成 `[0, 1)` 的数，也就是 `0.123312`、`0.982931`之类的，然后调用 `number` 的 toString方法将其转换成36进制的，按照MDN的说法，36进制的转换应该是包含了字母 `a~z` 和 数字`0~9`的，因为这样生成的是 `0.89kjna21sa` 类似这样的，所以要截取一下小数部分，即从索引 `2` 开始截取10个字符就是我们想要的随机字符串了

很多开源库都使用此方式为DOM元素创建随机ID。
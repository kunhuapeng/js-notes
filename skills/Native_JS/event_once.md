# 事件监听器只运行一次

如果你想添加一个事件监听器并且只运行一次，你可以使用 `once` 选项：

```js
element.addEventListener('click', () => {
    console.log('I run only once')
}, {
    once: true
});  
```


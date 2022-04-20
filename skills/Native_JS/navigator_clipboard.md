# 剪贴板操作

## 复制到剪贴板

可以使用 `Clipboard` API 创建“复制到剪贴板”功能：

```js
function copyToClipboard(text) {
    return navigator.clipboard.writeText(text);
}      
```

## 读取剪贴板

```js
function readFromClipboard() {
    return navigator.clipboard.readText();
}  
```

>`readText`和`writeText`的返回值都是promise


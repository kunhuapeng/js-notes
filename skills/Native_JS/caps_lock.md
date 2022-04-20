# 检查 Caps Lock 是否打开

您可以使用 `KeyboardEvent.getModifierState()` 来检测是否 `Caps Lock` 打开。

```js
const passwordInput = document.getElementById('password');

passwordInput.addEventListener('keyup', function (event) {
    if (event.getModifierState('CapsLock')) {
        // CapsLock 已经打开了
    }
});  
```


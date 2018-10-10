# ECMAScript

# DOM

# BOM

- 剪切板
```javascript
document.addEventListener('copy', function (event) {
    var clipboardData = event.clipboardData || window.clipboardData;
    if (!clipboardData) { return; }
    var text = window.getSelection().toString();
    if (text) {
        event.preventDefault();
        clipboardData.setData('text/plain', text + '\n\n鑫空间版权所有');
    }
});
```


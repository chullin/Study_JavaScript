## DOM 元素
`DOMContentLoaded` 這個元素會等 HTML 完全執行完後觸發，但不會等待 CSS、圖片等外部資源

使用 `document.addEventListener()`


我希望在 JS 載完 HTML 後，就會去抓 button 這個按鈕的 ID，然後按下
```JS
document.addEventListener("DOMContentLoaded", function(event) {
    document.getElementById("button").click()
});
``` 
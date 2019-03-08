<h2>主要技術</h2>
<p>1. css 變數宣告方法 <code>--變數名稱: 值;</code></p>
<pre>
    :root {
        --base: #ffc600;
        --spacing: 10px;
        --blur: 10px;
    }
</pre>
<p>2. CSS 變數使用方法 <code>var(--變數名稱)</code></p>
<p>3. <code>style.setProperty(屬性名稱, 值)</code> 可以設定 style 的屬性</p>
<p>4. <code>document.documentElement</code> 是根元素 <html>，因為 css 變數是在 html 底下，詳細可以用 <code>console.dir(document.documentElement)</code>查看</p>
<p>5. padding、blur 後面需要單位 px ，所以如果遇到就單位，沒有就空值</p>
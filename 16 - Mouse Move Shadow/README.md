<h2>技術解說</h2>
<p>1. 關於 ES6 的縮寫</p>
<pre>
    const {offsetWidth: width, offsetHeight: height} = hero    
</pre>
<p>可以看成</p>
<pre>
    const width = hero.offsetWidth
    const height = hero.offsetHeight
</pre>
<p>2. 修正 mousemove 時 target 變成子元素的問題</p>
<pre>
    if (e.target !== this) {
        x += e.target.offsetLeft
        y += e.target.offsetTop
    }
</pre>
<p>剩下的還好~~</p>
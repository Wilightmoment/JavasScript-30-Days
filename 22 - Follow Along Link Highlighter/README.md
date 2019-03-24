<h2>技術解說</h2>
<p>1. 創立反白色塊 highlight</p>
<pre>
    const highlight = document.createElement('span')
    highlight.classList.add('highlight')
    document.body.appendChild(highlight)
</pre>
<p>2. 針對所有 a 連結監聽 mouseenter 事件</p>
<p>駐: mouseover 會觸發所有子元素，mouseenter 只會觸發該元素</p>
<pre>
    triggers.forEach(a => a.addEventListener('mouseenter', highlightLink))
</pre>
<p>3. 取得該元素當前的位置資訊 <code>getBoundingClientRect</code></p>
<p>由於 <code>getBoundingClientRect</code> 是取得該元素對於當前視窗的相對位置</p>
<p>所以 top、left 要加上 <code>window.scrollX/Y</code>來取得實際位置</p>
<pre>
    const linkCoords = this.getBoundingClientRect()
    const coords = {
        width: linkCoords.width,
        height: linkCoords.height,
        top: linkCoords.top + window.scrollY,
        left: linkCoords.left + window.scrollX
    }
</pre>
<p>4. 設定 highlight 的位置與大小</p>
<pre>
    highlight.style.width = `${coords.width}px`
    highlight.style.height = `${coords.height}px`
    highlight.style.left = `${coords.left}px`
    highlight.style.top = `${coords.top}px
</pre>
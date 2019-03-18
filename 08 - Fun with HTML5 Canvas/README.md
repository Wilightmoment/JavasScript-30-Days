<h2>Canvas 解說</h2>
<p>1. <code>html</code> 中已經有 <code>canvas</code>，所以我們要取得它的 2d 內容，<code>canvas.getContext('2d')</code>，然後設定 cavnvas 的範圍
</p>
<pre>
    const canvas = document.querySelector('canvas')
    const ctx = canvas.getContext('2d')
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
</pre>
<p>2. <code>ctx.lineJoin = 'round'</code>設定兩線相交的樣式</p>
<p>3. <code>ctx.lineCap = 'round'</code>設定結束端點的樣式</p>
<p>4. <code>ctx.beginPath()</code>開始繪圖</p>
<p>5. <code>ctx.moveTo(lastX, lastY)</code>設定起點</p>
<p>6. <code>ctx.lineTo(e.offsetX, e.offsetY)</code>欲繪製到的位置</p>
<p>7. <code>ctx.strokeStyle = '#BADA55'</code>設定線條的顏色</p>
<p>8. <code>ctx.lineWidth = 100</code>設定線條寬度</p>
<h2>大致步驟說明</h2>
<p>先取得滑鼠第一次點擊的位置</p>
<pre>
    canvas.addEventListener('mousedown', (e)=> {
        isDraw = true
        lastX = e.offsetX
        lastY = e.offsetY
    })
</pre>
<p>接著繪製到滑鼠當前的位置</p>
<pre>
    function draw(e) {
        if (!isDraw) return //不是繪圖中的話就跳離
        
        ctx.beginPath()
        ctx.moveTo(lastX, lastY)
        ctx.lineTo(e.offsetX, e.offsetY)
        ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`
        ctx.stroke()

        lastX = e.offsetX //最後記得將滑鼠座標更新
        lastY = e.offsetY
    }
</pre>

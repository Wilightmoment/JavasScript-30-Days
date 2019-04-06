<h2>技術解說</h2>
<p>1. 先取得滑鼠點擊位置與 slider 當前滾動多少</p>
<pre>
    const slider = document.querySelector('.items')
    let isDrag = false, scrollLeft, startX

    slider.addEventListener('mousedown', (e) => {
        isDrag = true
        slider.classList.add('active')
        startX = e.pageX //取得滑鼠點擊位置
        scrollLeft = slider.scrollLeft  //紀錄當前滾動多少距離
    })
</pre>
<p>2. 滑鼠按住並拖曳時，移動 slider</p>
<pre>
    slider.addEventListener('mousemove', (e) => {
        if (!isDrag) return;
        e.preventDefault()
        // 滑鼠移動位置差 = scroll 移動距離
        const walk = (e.pageX - startX) * 2
        // 由於往左滑時，walk 會是負的，所以要用減的
        slider.scrollLeft = scrollLeft - walk 
    })
</pre>
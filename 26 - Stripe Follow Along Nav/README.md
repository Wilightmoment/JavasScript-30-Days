<h2>技術解說</h2>
<p>1. 針對每個 li 進行監聽</p>
<pre>
    const triggers = document.querySelectorAll('.cool > li')
    triggers.forEach(trigger => trigger.addEventListener('mouseenter', handleEnter))
    triggers.forEach(trigger => trigger.addEventListener('mouseleave', handleLeave))
</pre>
<p>2. 滑鼠移入時，新增 class</p>
<p>class 都寫好 CSS 所以只要新增/刪除 class 名稱就好</p>
<pre>
    function handleEnter() {
        this.classList.add('trigger-enter')
        // 確保 trigger-enter 已被加上，才繼續新增 trigger-enter-active
        setTimeout(() => this.classList.contains('trigger-enter') && this.classList.add('trigger-enter-active'), 150)
        background.classList.add('open')           
    }
</pre>
<p>3. 用 <code>getBoundingClientRect()</code> 取得顯示內容的位置屬性</p>
<p>當 nav 上方多出內容時，會導致 dropdown 往下擠，所以要減掉多出的高度</p>
<pre>
    const dropdown = this.querySelector('.dropdown')
    const dropdownCoords = dropdown.getBoundingClientRect()
    const navCooords = nav.getBoundingClientRect()
    const coords = {
        width: dropdownCoords.width,
        height: dropdownCoords.height,
        top: dropdownCoords.top - navCooords.top,
        left: dropdownCoords.left - navCooords.left
    }
    background.style.setProperty('width', `${coords.width}px`)
    background.style.setProperty('height', `${coords.height}px`)
    background.style.setProperty('transform', `translate(${coords.left}px, ${coords.top}px)`)
</pre>
<p>4. 移除 class</p>
<pre>
    function handleLeave() {
        this.classList.remove('trigger-enter', 'trigger-enter-active')
        background.classList.remove('open')
    }
</pre>
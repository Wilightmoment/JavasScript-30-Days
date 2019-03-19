<h2>流程說明</h2>
<p>1. 將每次的選取都視為最後一次選取，並記錄下來</p>
<pre>
    function handleClick (e) {
        ...
        lastClick = this    
    }
</pre>
<p>2. 利用<code>e.shiftKey</code> 判斷是否有按住 shift 鍵</p>
<p>3. 判斷最後一次選取的 checkbox 和按住 shift 點選的 checkbox 是哪兩個</p>
<pre>
    checkboxes.forEach(checkbox => {
        console.log(checkbox)
        if (checkbox === this || checkbox === lastClick) {
            isBetween = !isBetween
            console.log('prepare')
        }
    })
</pre>
<p>4. 如果在範圍內 <code>isBetween</code> 就將 checkbox 選取</p>
<pre>
    if (isBetween) {
        checkbox.checked = true
    }
</pre>
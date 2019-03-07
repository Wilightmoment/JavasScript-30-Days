# Drum Kit
<h2>主要語法</h2>
<p>
    1. 利用<code>addEventListener()</code>來進行事件的綁定
    2. <code>document.querySelector(`audio[data-*=""]`)</code> 可以抓到指定的 data-* 屬性元素
    3. audio 屬性中的 currentTime 可以重置播放時間
    <pre><code>audio.currentTime = 0</code></pre>
    4. <code>transitionend</code> 事件可以監聽 transition 結束後的行為
    <pre>
        keys.forEach(key => key.addEventListener('transitionend', removePlayingClass))
        
        function removePlayingClass (e) {
            if (e.propertyName!=='transform') return
            e.target.classList.remove('playing')    
        }
    </pre>
</p>

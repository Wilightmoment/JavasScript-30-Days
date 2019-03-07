# Drum Kit
<h2>主要語法</h2>
<p>
    1. 利用<code>addEventListener()</code>來進行事件的綁定 <br>
    2. <code>document.querySelector(`audio[data-*=""]`)</code> 可以抓到指定的 data-* 屬性元素<br>
    3. audio 屬性中的 currentTime 可以重置播放時間<br>
    <pre><code>audio.currentTime = 0</code></pre><br>
    4. <code>transitionend</code> 事件可以監聽 transition 結束後的行為<br>
    <pre>
        keys.forEach(key => key.addEventListener('transitionend', removePlayingClass))
        
</p>

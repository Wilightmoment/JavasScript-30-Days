<h2>主要技術</h2>
<p>這篇其實沒什麼好說的，就跟 <a href="https://github.com/Wilightmoment/JavasScript-30-Days/tree/master/11%20-%20Custom%20Video%20Player">Day11</a> 差不多</p>
<pre>
    const speed = document.querySelector('.speed')
    const bar = speed.querySelector('.speed-bar')
    const video = document.querySelector('video')
    
    speed.addEventListener('mousemove', (e) => {
        const percent = e.offsetY / speed.offsetHeight
        const min = 0.4
        const max = 4
        const height = Math.round(percent * 100) + '%'
        const playbackRate = percent * (max - min) + min
        bar.style.height= height
        bar.textContent = playbackRate.toFixed(2) + 'x'
        video.playbackRate = playbackRate
    })
</pre>
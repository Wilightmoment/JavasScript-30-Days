<h2>技術解說</h2>
<p>1. 處理播放</p>
<pre>
    video.addEventListener('click', togglePlay)
    function togglePlay () {
        //先判斷當前狀態再決定要播放還是暫停
        const method = video.paused ? 'play' : 'pause';
        video[method]();
    }
</pre>
<p>2. 更新播放按鈕</p>
<pre>
    video.addEventListener('play', updateButton)
    video.addEventListener('pause', updateButton)
    function updateButton () {  
        const icon = video.paused ? '►' : '❚ ❚';
        toggle.textContent = icon;
      }
</pre>
<p>3. 處理音量控制與播放速度</p>
<pre>
    ranges.forEach(range => range.addEventListener('change', handleRangeUpdate))
    ranges.forEach(range => range.addEventListener('mousemove', handleRangeUpdate))
    function handleRangeUpdate () {
        //這裡 this.name 會抓到該 range 的名稱
        //例如調整音量會變成 video.volumn = 1
        video[this.name] = this.value
    }
</pre>
<p>4. 快進與倒退</p>
<pre>
    skipButtons.forEach(button => button.addEventListener('click', skip))
    function skip () {
        //dataset.* 可以取得 html 中 data-* 屬性的值
        video.currentTime += parseFloat(this.dataset.skip)
    }
</pre>
<p>5. 進度條顯示</p>
<pre>
    //監聽 video 的 'timeupdate' 事件來調整進度條
    video.addEventListener('timeupdate', handleProgress)
    function handleProgress () {
        //單純換算百分比，屬性可以透過 console.dir()查看
        const percent = this.currentTime / this.duration * 100
        //progressBar 的 display 是 flex，所以這裡透過 flex-basis 調整
        progressBar.style.flexBasis = `${percent}%`
    }
</pre>
<p>6. 拖曳進度條改變當前播放進度</p>
<pre>
    let mousedown = false
    progress.addEventListener('click', scrub)
    //如果單純監聽 mousemove 會導致滑鼠移入時不斷改變，所以多了一個 mousedown
    //來判斷滑鼠是否"是按住拖曳"
    progress.addEventListener('mousemove', (e)=> mousedown && scrub(e))
    progress.addEventListener('mousedown', () => mousedown = true)
    progress.addEventListener('mouseup', () => mousedown = false)
        
    function scrub (e) {
        //滑鼠點擊位置 / progress 的總長度 * video 的時長
        const scrubTime = e.offsetX / progress.offsetWidth * video.duration
        video.currentTime = scrubTime
    }
</pre>
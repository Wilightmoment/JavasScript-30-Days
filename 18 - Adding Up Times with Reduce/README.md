<h2>這次複習 <code>map、reduce</code>，透過兩個陣列的 function 來計算所有 vedio 的時間</h2>
<p>下方程式碼步驟說明</p>
<p>1. 取得所有元素 timeNodes</p>
<p>2. 取得所有的 data-time</p>
<p>3. 將 data-time 透過 <code>split()</code> 拆成 min、sec</p>
<p>4. 將 min、sec 轉成數值並換算成秒數回傳</p>
<p>5. 將所有的秒數用 <code>reduce</code>進行加總</p>
<pre>
    const timeNodes = Array.from(document.querySelectorAll('[data-time]'))
    const seconds = timeNodes.map(node => node.dataset.time).map(time => {
        const [min, sec] = time.split(':').map(parseFloat)
        return min * 60 + sec
    }).reduce((total, seconds)=> {return total + seconds}, 0)
</pre>
<p>6. 最後就是簡單的數學</p>
<pre>
    let secondsLeft = seconds
    const hours = Math.floor(secondsLeft / 3600)
    secondsLeft = secondsLeft % 3600
    const mins =  Math.floor(secondsLeft / 60)
    secondsLeft = secondsLeft % 60
    console.log(hours, mins,secondsLeft)
</pre>
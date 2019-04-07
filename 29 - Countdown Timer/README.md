<h2>主要技術</h2>
<p>這次要做簡單的倒數計時，主要利用 <code>setInterval(function, milliseconds)</code> 與 <code>clearInterval(var)</code></p>
<pre>
    function timer(seconds) {
        clearInterval(countdown) //先清除一開始還在執行的 Interval
        const now = Date.now() //取得當前時間戳記
        const then = now + seconds * 1000 //取得目標時間戳記
        //顯示時間，由於 setInterval 會先等一秒再開始，導致第一秒不會顯示
        //所以這裡要先顯示被跳過的時間
        displayTimeLeft(seconds) 
        displayEndTime(then)
        countdown = setInterval(() => { //用 setInterval 執行倒數行為
            const secondsLeft = Math.round((then - Date.now()) / 1000)
            if (secondsLeft < 0) { //清除 Interval 的條件
                clearInterval(countdown)
                return;
            }
            displayTimeLeft(secondsLeft)
        }, 1000)
    }
</pre>
<p>顯示時間</p>
<pre>
    function displayTimeLeft(seconds) {
        const min = ~~(seconds / 60)
        const remainderSeconds = seconds % 60
        const display = `${min}:${remainderSeconds < 10 ? '0' : ''}${remainderSeconds}`
        timerDisplay.textContent = display
    }
</pre>
<p>如果有 form 表單的話，可以用 document 去抓取表單名稱來進行操作</p>
<pre>
    <form name="customForm" id="custom">
        <input type="text" name="minutes" placeholder="Enter Minutes">
    </form>
    document.customForm.addEventListener('submit', function(e) {
        e.preventDefault()
        const mins = this.minutes.value
        timer(mins * 60)
        this.reset()
    })
</pre>
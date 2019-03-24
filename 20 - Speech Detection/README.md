<h2>技術解說</h2>
<p>這篇也需要用到 webServer</p>
<p>一開始先呼叫語音API，有多 <code>webkit 是 Chrom 的</code></p>
<pre>
    window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition
</pre>
<p>接著建立語音物件</p>
<p><code>recognition.interimResults</code>設定是否回傳判斷中的文字，如果為 false 則只會回傳最終判斷文字</p>
<p><code>recognition.lang</code> 設置判斷語言</p>
<pre>
    const recognition = new SpeechRecognition()
    recognition.interimResults = true
    recognition.lang = 'zh-TW'
</pre>
<p>啟動語音辨識</p>
<pre>recognition.start()</pre>
<p>監聽語音內容</p>
<pre>
    recognition.addEventListener('result', e => {
        //取得語音文字
        const transcript = Array.from(e.results).map(result => result[0]).map(result => result.transcript).join('')
        console.log(transcript)
    
        p.textContent = transcript
    
        //當講完一句話時，即判斷完成
        if (e.results[0].isFinal) {
            p = document.createElement('p')
            words.appendChild(p)
        }
    
    })
</pre>
<p>判斷完成後再次啟動語音辨識</p>
<pre>recognition.addEventListener('end', recognition.start)</pre>
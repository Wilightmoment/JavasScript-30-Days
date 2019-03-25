<h2>技術解說</h2>
<p><code>SpeechSynthesisUtterance()</code> 可以建立想要說的話、速度、語音等</p>
<pre> const msg = new SpeechSynthesisUtterance()</pre>
<p><code>window.speechSynthesis</code> 可以操控 <code>utterance </code>的行為</p>
<pre>
    speechSynthesis.cancel() //取消播放
    speechSynthesis.speak(msg) //播放指定的語音內容
    speechSynthesis.getVoices() //取得所有語音
</pre>

<p>1. 先取得所有可用的語音</p>
<pre>
    speechSynthesis.addEventListener('voiceschanged', populateVoices)
    function populateVoices () {
        voices = this.getVoices()
        voicesDropdown.innerHTML = voices.map(voice => {
          return `<option value="${voice.name}">${voice.name} ${voice.lang}</option>`
        }).join('')
    }
</pre>
<p>2. 設定想聽的語音</p>
<pre>
    voicesDropdown.addEventListener('change', setVoice)
    function setVoice () {
        msg.voice = voices.find(voice => voice.name === this.value)
        toggle() //播放聲音
    }
</pre>
<p>3. 播放語音</p>
<pre>
    function toggle (startOver = true) {
        speechSynthesis.cancel()
        if (startOver) {
            speechSynthesis.speak(msg)
        }
    }
</pre>
<p>4. 設定語音速率、音頻等</p>
<pre>
    options.forEach(option => option.addEventListener('change', setOption))
    function setOption () {
        console.log(this.name,this.value)
        msg[this.name] = this.value
        toggle()
    }
</pre>

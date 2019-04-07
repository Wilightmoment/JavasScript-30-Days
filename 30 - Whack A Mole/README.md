<h2>主要技術</h2>
<p>1. 先建立亂數函式方便之後使用</p>
<pre>
    function randomTime (min, max) {
        return Math.round(Math.random() * (max - min) + min)
    }
</pre>
<p>2. 隨機選取一個洞</p>
<p>為了避免下一個與上一個重複，所以用 lastHole 來紀錄上一個洞</p>
<pre>
    function randomHole (holes) {
        const index = ~~(Math.random() * holes.length)
        const hole = holes[index]
        if (lastHole === hole) {
          console.log('repeat!')
          return randomHole(holes)
        }
        lastHole = hole
        return hole
    }
</pre>
<p>3. 彈出地鼠</p>
<pre>
    function peep () {
        const time = randomTime(200, 1000)
        const hole = randomHole(holes)
    
        hole.classList.add('up')
        setTimeout(() => { 每個地鼠有自己出現的時間
          hole.classList.remove('up')
          if (!timeUp) peep() //時間到才停止彈出地鼠
        }, time)
    }
</pre>
<p>4. 點擊地鼠取得分數</p>
<p><code>e.isTrusted</code> Event 介面的唯獨屬性布林值，若事件是由使用者操作產生，則為 true。反之。</p>
<p>由於點擊地鼠是由使用者產生的事件，所以這裡的 isTrusted 會是 true</p>
<pre>
    moles.forEach(mole => mole.addEventListener('click', bonk))
    function bonk(e) {
        if (!e.isTrusted) return;
        score++
        this.parentNode.classList.remove('up')
        scoreBoard.textContent = score
    }
</pre>
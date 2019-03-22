<h2>技術解說</h2>
<p>以前有流行一種網頁是需要頁按下特定的按鍵才會出現</p>
<p>像是輸入"上上下下左左右右AB"，就會跳出密技一樣</p>
<p>1. 先建立答案與存放陣列</p>
<pre>
    const pressed = [];
    const secretCode = 'wesbos';
</pre>
<p>2. 在 window 下監聽事件</p>
<pre>
    window.addEventListener('keyup', (e) => {
        ...在此撰寫
    })
</pre>
<p>3. 將輸入的 key 存放在陣列中，並保持陣列只有"最新的六個字"</p>
<p><i>註: 因為答案只有六個字</i></p>
<pre>
    pressed.push(e.key)
    pressed.splice(-secretCode.length-1, pressed.length - secretCode.length)    
    if (pressed.join('').includes(secretCode)) {
        cornify_add(); //引入的 JS 的 function
    }
</pre>
<p><code>splice(start, delete)</code>如果 start 是負值就會從最後開始，delete 如果是負值就不會刪除</p>
<p>start = -1 表示最後一個字，所以這裡要從 -7 開始刪除(由後往前數，從第七個數字開始刪除)</p>
<p>-7 這裡寫成 <code>-secretCode.length-1</code> 可以動態計算位置</p>
<p>至於 delete，只要陣列長度一超過答案的長度就馬上刪除，所以是 <code>pressed.length - secretCode.length</code></p>
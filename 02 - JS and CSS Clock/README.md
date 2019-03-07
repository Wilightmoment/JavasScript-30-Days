<h2>主要技術</h2>
<p>1. <code>transform-origin</code> 可以改變旋轉的軸心</p>
<p>2. 關於要轉幾度 : 先將取得的秒數轉換成百分比，乘上 360 (一圈360度)，最後再加上 90 (因為一開始先轉了 90 度)</p>
<pre>const secondsDegree = ((seconds / 60) * 360) + 90</pre>
<p>3. 解決當指針歸零時，會跳一圈的問題- <br>由於 <code>transition</code> 的關係，所以要在0秒的時候暫時移除 <code>transition</code></p>
<pre>(seconds === 0) ? hands.forEach(hand=>hand.style.transition='all 0s') : hands.forEach(hand=>hand.style.transition='all 0.05s cubic-bezier(0, 2.67, 0.35, 1.05)')</pre>
<p>上方是三原判斷式，"?"前面是條件，後方是 true 時的動作，":"後面接的是 false 時的動作</p>
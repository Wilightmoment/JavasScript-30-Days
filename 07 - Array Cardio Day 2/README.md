<h2>介紹 array 常用的方法-2</h2>
<p>1. <code>Array.prototype.some()</code>會回傳陣列中是否有任一元素達成條件</p>
<pre>const isAdult = people.some(person => (new Date).getFullYear() - person.year >= 19)</pre>
<p>2. <code>Array.prototype.every()</code>會回傳陣列中每個元素是否皆達成條件</p>
<pre>const allAdult = people.every(person => (new Date).getFullYear() - person.year >= 19)</pre>
<p>3. <code>Array.prototype.find()</code>會回傳找到的物件，跟 <code>filter()</code> 類似，但是 <code>find()</code> 只會回傳一筆</p>
<pre>const comment = comments.find(comment => comment.id === 823423)</pre>
<p>4. <code>Array.prototype.findIndex()</code>與 <code>find() </code>類似，但回傳的是 index</p>
<pre>const index = comments.findIndex(index => index.id === 823423)</pre>
<p>5. <code>Array.prototype.splice(index, num)</code>刪除陣列中的元素，第一個參數為開始刪除的位置，第二個參數是數量</p>
<p>6. <code>Array.prototype.slice(start, end)</code> 回傳一個從 start 開始，end 結束的陣列 //不含 end</p>
<pre>const newComments = [...comments.slice(0, index), ...comments.slice(index+1)]</pre>
<p>上面用到了 ES6 的解構覆值</p>
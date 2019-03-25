<h2>本次介紹 Event Bubbling </h2>
<p><code>EventTarget.addEventListener('eventName', callback, option)</code>其實有三個參數，其中 <code>option</code> 的可操作屬性如下</p>
<pre>
    divs.forEach(div => div.addEventListener('click', logText, {
        capture : false,
        once : false,
    }));
</pre>
<p><code>capture</code> 預設為 false，表示事件的觸發是由內而外，反之。</p>
<p><code>once</code> 預設為 false，若為 <code>true</code>則事件只會觸發一次</p>
<p>如果在 function 中加入<code>e.stopPropagation()</code>則會停止觸發 bubble 事件</p>
<pre>
    function logText(e) {
        e.stopPropagation(); // stop bubbling!
    }
</pre>
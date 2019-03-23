<h2>這次是複習 sort 的用法</h2>
<p>1. 我們要針對陣列內容進行排序，不過要先過濾開頭是 a 或 an 或 the 的文字</p>
<pre>
    function strip(bandName) {
        return bandName.replace(/^(a |the |an )/i, '').trim();
    }
</pre>
<p>2. 利用 <code>sort()</code>排序</p>
<pre>
    const sortedBands = bands.sort((a, b) => strip(a) > strip(b) ? 1 : -1);
</pre>
<p>3. 顯示排序後的結果</p>
<pre>
    document.querySelector('#bands').innerHTML =
    sortedBands
        .map(band => `<li>${band}</li>`)
        .join('');
</pre>
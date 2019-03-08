<h2>主要技術</h2>
<p>1. 用 <code>fetch()</code>來撈資料，他是 JS 原生的語法，並實作了 <code>Promise</code></p>
<pre>fetch(endpoint).then(blob => blob.json()).then(data => cities.push(...data))</pre>
<p>2. <code>RegExp()</code>正規表達式，可以找到匹配的文字</p>
<p>3. <code>match()</code>會回傳指定的字串</p>
<pre>
    function findMatches(wordToMatch, cities) {
        return cities.filter(place => {
          const regex = new RegExp(wordToMatch, 'gi') //g 表示 global， i 表示不分大小寫
          return place.city.match(regex) || place.state.match(regex)
        })
      }
</pre>
<p>4. <code>replace()</code>會取代指定的字串</p>
<pre>const cityName = place.city.replace(regex, `<span class="hl">${this.value}</span>`)</pre>

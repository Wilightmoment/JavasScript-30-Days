<h2>這篇介紹 array 常用的方法</h2>
<p>1. <code>filter()</code> 會過濾原陣列中條件為 true 的元素並構成新的陣列。</p>
<pre>const fifteen = inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600))</pre>
<p>2. <code>map()</code> 會回傳一個新的陣列，該內容是回呼函式運算後的集合</p>
<pre>const fullNames = inventors.map(inventor => `${inventor.first} ${inventor.last}`)</pre>
<p>3. <code>sort()</code> 會對陣列中的元素進行排序，如果回傳的值小於 0，則會將 a 放到 b 的前邊，反之。</p>
<pre>const ordered = inventors.sort((a, b) => a.year > b.year ? 1 : -1)</pre>
<p>4. <code>reduce()</code> 將累加器與陣列中的所有元素"依序"傳入回呼函式，最後回傳單一值</p>
<p><code>arr.reduce(callback[accumulator, currentValue, currentIndex, array], initialValue)</code>
    累加器(accumlator) 一開始要給予初始值(initialValue)
</p>
<pre>
const totalYears = inventors.reduce((total, inventor) => {
    return total + (inventor.passed - inventor.year);
}, 0);
</pre>
<p>5. <code>sort()</code> 的應用，根據年齡進行排序(由大到小)</p>
<pre>
const oldest = inventors.sort(function(a, b) {
    const lastInventor = a.passed - a.year;
    const nextInventor = b.passed - b.year;
    return lastInventor > nextInventor ? -1 : 1;
});
</pre>
<p>6. <code>map() + filter()</code> 的應用。尋找所有 a 連結中包含 'de' 的內容</p>
<p>由於 document.querySelectorAll() 回傳的是 NodeList，所以要先透過 Array.from() 轉成陣列，才可以使用 map()、filter() 等 prototype</p>
<pre>
    const category = document.querySelector('.mw-category');
    const links = Array.from(category.querySelectorAll('a'));
    const de = links
                .map(link => link.textContent)
                .filter(streetName => streetName.includes('de'));
</pre>
<p>7. <code>sort()</code> 應用，根據人名進行排序</p>
<pre>
    const alpha = people.sort((lastOne, nextOne) => {       
        const [aLast, aFirst] = lastOne.split(', ');
        const [bLast, bFirst] = nextOne.split(', ');
        return aLast > bLast ? 1 : -1;
    });
</pre>
<p>8. <code>reduce()</code> 應用。計算陣列中每個元素出現幾次，並回傳一個物件</p>
<pre>
    const transportation = data.reduce((obj, item)=> {
        !obj[item] ? obj[item] = 1 : obj[item]++;
        return obj;
    }, {})
</pre>
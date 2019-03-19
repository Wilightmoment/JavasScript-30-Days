<h2>常用的 dev tools</h2>
<p>1. <code>console.log()</code>印出想要呈現的內容 <code>console.log('test')</code></p>
<p>也可以用插入的方式呈現， <code>console.log('Hello I am a %s string!', '💩')</code></p>
<p>或是加入 css，<code>console.log('%c I am some great text', 'font-size:50px; background:red; text-shadow: 10px 10px 0 blue')</code></p>
<p>2. <code>console.warn()、console.info()、console.error()</code> 用法與 <code>console.log()</code> 相同，但是多了警示符號</p>
<P>3. <code>console.assert(boolean, text)</code> 當第一個參數為 false 時，會印出第二個參數的內容</P>
<pre>
    const p = document.querySelector('p')
    console.assert(p.classList.contains('ouch'), 'That is wrong!')
</pre>
<p>4. <code>console.clear()</code>清除所有 console 內容</p>
<p>5. <code>console.dir()</code> 會列出所有 available property</p>
<p>6. <code>console.group()</code> 可以將 console 群組化，在開頭與結尾使用相同的參數名稱</p>
<pre>
    dogs.forEach(dog => {
        console.groupCollapsed(`${dog.name}`)
        console.log(`This is ${dog.name}`)
        console.log(`${dog.name} is ${dog.age} years old`)
        console.log(`${dog.name} is ${dog.age * 7} dog years old`)
        console.groupEnd(`${dog.name}`)
    })
</pre>
<p>7. <code>console.count()</code>會計算出現的次數</p>
<p>8. <code>console.time()</code>會計算開始到結束總共花費的時間</p>
<pre>
    console.time('fetching data')
    fetch('https://api.github.com/users/wesbos')
      .then(data => data.json())
      .then(data => {
        console.timeEnd('fetching data')
        console.log(data)
    });
</pre>
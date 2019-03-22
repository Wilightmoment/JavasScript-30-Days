<h2>說明 by references 與 by value</h2>
<p>1. 只要是變數(數字、字串、布林)都是 by value</p>
<p>當指定 <code>age2 = age</code> 時，age2 會指向新的記憶體位置再賦予值</p>
<p>所以更動 age2 時，age 不會跟著改變</p>
<pre>
    let age = 100
    let age2 = age
    console.log(age, age2) // 100, 100
    age = 200
    console.log(age, age2) // 100, 200
</pre>
<p>2. 而物件、陣列都是 by references</p>
<p><code>team = players</code> team 與 players 都會指向相同的記憶體位置</p>
<p>所以改動 team 時，players 也會跟著改變</p>
<pre>
    const players = ['Wes', 'Sarah', 'Ryan', 'Poppy']
    const team = players
    team[3] = 'Lux'
    console.log(players, team) //['Wes', 'Sarah', 'Ryan', 'Lux'], ['Wes', 'Sarah', 'Ryan', 'Lux']
</pre>

<h2>以下介紹幾種複製陣列的方式(指向新的記憶體位置)</h2>
<p>1. <code>Array.prototype.slice()</code>，它會回傳一個新的陣列</p>
<pre>const team2 = players.slice()</pre>
<p>2. <code>Array.prototype.concat()</code>，它會合併兩個陣列，並回傳新的陣列</p>
<pre>const team3 = [].concat(players)</pre>
<p>3. ES6 的 spread 方法</p>
<pre>const team4 = [...players]</pre>
<p>4. <code>Array.from()</code>，它會建立新的陣列實體</p>
<pre>const team5 = Array.from(players)</pre>

<h2>以下介紹幾種複製物件的方式(指向新的記憶體位置)</h2>
<p>我們先假設有一個陣列: </p>
<pre>
    const wes = {
        name: 'Wes',
        age: 100,
        social: {
          twitter: '@wesbos',
          facebook: 'wesbos.developer'
        }
    };
</pre>
<p>1. <code>Object.assign(target, ...sources)</code>它會複製一個或多個物件到目標物件(target)</p>
<p>不過要注意的是<code>Object.assign()</code>只會複製第一層，第二層之後都是 by references</p>
<p>也就是說 dev 物件中 social 內的屬性都是 by references</p>
<p>改動 web.social 的話，dev.social 也會跟著改變</p>
<pre>
    const dev = Object.assign({}, wes)
</pre>

<p>2. 先將物件轉成 JSON 文字，再將 JSON 文字轉成物件</p>
<p>這種做法會完全複製物件，也就是俗稱的 Deep Copy</p>
<p>即使改動 web.social，dev.social 也不會改變</p>
<pre>
    const dev2 = JSON.parse(JSON.stringify(wes))
</pre>
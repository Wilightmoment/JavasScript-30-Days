<h2>技術解說</h2>
<p>1. 首先監聽 <code>submit</code>事件，並透過 <code>e.preventDefault()</code>取消表單預設事件</p>
<pre>
    addItems.addEventListener('submit', addItem)
    function addItem (e) {
        e.preventDefault()
        ...
    }
</pre>
<p>2. 將資料存成物件並放入陣列中</p>
<pre>
    const text = this.querySelector('[name=item]').value
    const item = {
      text, // 這是 ES6 的寫法，也可以寫成這樣 text: text
      done: false
    }
    items.push(item)
    this.reset() //這是表單的 function，可以清除表單內容
</pre>
<p>3. 將陣列放入 localStorage 中</p>
<p>註: 由於 localStorage 只能存放字串，所以要先轉成字串</p>
<pre>
    localStorage.setItem('items', JSON.stringify(items))
</pre>
<p>4. 將內容寫到畫面中</p>
<pre>
    function populateList (items, itemsList) {
        itemsList.innerHTML = items.map((item, i) => {
          return `
            <li>
              <input type="checkbox" data-index=${i} id="item${i}" ${item.done ? 'checked' : ''} />
              <label for="item${i}">${item.text}</label>
            </li>
          `
        }).join('')
      }
</pre>
<p>5. checkbox 點選時，也要重新寫入 localStorage 中</p>
<pre>
    itemsList.addEventListener('click', toggleDone)
    function toggleDone (e) {
        if (!e.target.matches('input')) return; //避免觸發到的不是 input 
        const index = e.target.dataset.index
        items[index].done = !items[index].done
        localStorage.setItem('items', JSON.stringify(items))
        populateList(items, itemsList)
    }
</pre>
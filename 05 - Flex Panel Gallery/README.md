<h2>主要技術</h2>
<p>關於 <code>flex</code>可以參考<a href="https://wcc723.github.io/css/2017/07/21/css-flex/">卡斯柏的文章</a></p>
<p>剩下就是運用前面所提到的<code>transitionend</code>事件</p>
<pre>
    function toggleActive(e) {
        // console.log(e.propertyName)
        if (e.propertyName.includes('flex')) {
            this.classList.toggle('open-active')
        }
    }
</pre>

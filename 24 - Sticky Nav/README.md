<h2>技術解說</h2>
<p>1. 當 <code>window.scrollY</code>大於 <code>nav.offsetTop</code>時，新增 <code>.fixed-nav</code>來修正 nav 的位置</p>
<pre>
const nav = document.querySelector('#main')
const topOfNav = nav.offsetTop

function sticky () {
  if (window.scrollY >= topOfNav) {    
    document.body.classList.add('fixed-nav')
  } else {
    document.body.classList.remove('fixed-nav')
  }
}
window.addEventListener('scroll', sticky)
</pre>
<p>css 部分</p>
<pre>
    .fixed-nav nav {
        position: fixed;
    }
</pre>
<p>2. 由於將 nav 的 position 改成 fixed，導致失去原有的高度，所以要進行修正</p>
<pre>
    if (window.scrollY >= topOfNav) {
        document.body.style.paddingTop = nav.offsetHeight + 'px'
        ...
      } else {
        document.body.style.paddingTop = 0
        ...
    }
</pre>
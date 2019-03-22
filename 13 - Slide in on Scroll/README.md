<h2>技術解說</h2>
<p>1. <code>window.scrollY</code>可以抓到視窗最上方的位置</p>
<p>所以我們只要加上視窗的高度再減掉想要滑入的圖片的一半高度，就剛好會是滑到該圖片的位置</p>
<pre>
    const slideAt = (window.scrollY + window.innerHeight) - sliderImage.height / 2
</pre>
<p>講起來有點饒，實際想一下就會知道了</p>
<p>2. 找到圖片的底端</p>
<pre>const imageBottom = sliderImage.offsetTop + sliderImage.height</pre>
<p>如此一來我們就能判斷當前畫面是有要顯示圖片</p>
<pre>
        const isHalfShown = slideAt > sliderImage.offsetTop
        const isNotScrolledPast = window.scrollY < imageBottom
        if (isHalfShown && isNotScrolledPast) {
          sliderImage.classList.add('active')
        } else {
          sliderImage.classList.remove('active')
        }
      })
</pre>
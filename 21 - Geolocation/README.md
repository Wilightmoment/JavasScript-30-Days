<h2>技術解說</h2>
<p>這次的操作需要在手機上才有辦法看到，請用手機模擬器或在手機上開啟</p>
<p>1. <code>Navigator.geolocation.getPosition()</code>取得一次當前地理位置</p>
<p>2. <code>Navigator.geolocation.watchPosition(data, err)</code>監聽當前地理位置</p>
<pre>
    navigator.geolocation.watchPosition((data) => {
        console.log(data);
        speed.textContent = data.coords.speed;
        // heading 是目前的指向
        arrow.style.transform = `rotate(${data.coords.heading}deg)`;
      }, (err) => {
        console.error(err);
    });
</pre>
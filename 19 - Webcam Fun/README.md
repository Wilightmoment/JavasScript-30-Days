<h2>技術解說</h2>
<p>這個專案要再 Web Server 上執行</p>
<p>1. 先取得 camera 的影像 <code>navigator.mediaDevices.getUserMedia</code></p>
<p>由於 <code>navigator.mediaDevices.getUserMedia</code>實作 <code>promise</code>所以要用 <code>then</code>來接</p>
<pre>
    function getVideo() {
        navigator.mediaDevices.getUserMedia({ video: true, audio: false })
          .then(localMediaStream => {
            console.log(localMediaStream);
                      
            video.srcObject = localMediaStream;
            video.play();
          })
          .catch(err => {
            console.error(`OH NO!!!`, err);
          });
    }
</pre>
<p>2. 將影像丟到 canvas 上呈現</p>
<pre>
    function paintToCanvas() {
        const width = video.videoWidth;
        const height = video.videoHeight;
        canvas.width = width;
        canvas.height = height;
      
        return setInterval(() => {
            //將影像畫出
          ctx.drawImage(video, 0, 0, width, height);
        }, 16);
    }
</pre>
<p>3. 監聽 canplay 事件</p>
<p>這樣當 video 可以被偵測時，就會直接執行</p>
<pre>
    video.addEventListener('canplay', paintToCanvas)
</pre>
<p>4. 儲存(下載)照片</p>
<pre>
    function takePhoto() {
        // 播放拍照的音效
        snap.currentTime = 0;
        snap.play();
      
        // 先將 canvas 存成 dataURL 的格式
        const data = canvas.toDataURL('image/jpeg');
        // 然後將它放到一個新的 a 連結上
        const link = document.createElement('a');
        link.href = data;
        // 設成 download 就可以下載，第二個參數是下載名稱
        link.setAttribute('download', 'handsome');
        link.innerHTML = `<img src="${data}" alt="Handsome Man" />`;
        strip.insertBefore(link, strip.firstChild);
    }
</pre>
<p>5. 渲染影像</p>
<p>在原本的 <code>paintToCanvas()</code> 新增動作</p>
<pre>
    function paintToCanvas() {
       ...      
        return setInterval(() => {
          ...
          // 取的 canvas 畫面資訊然後另外處理它們
          let pixels = ctx.getImageData(0, 0, width, height);
          // 渲染模式1 - redEffect
          // pixels = redEffect(pixels);
      
          // 渲染模式2 - rgbSplit
          //pixels = rgbSplit(pixels);
          // ctx.globalAlpha = 0.8;
      
          // 渲染模式3 - greenScreen
          // pixels = greenScreen(pixels);

          // 處理完之後再放回來
          ctx.putImageData(pixels, 0, 0);
        }, 16);
    }
</pre>
<p>這邊舉例其中一個 <code>redEffect</code></p>
<pre>
    function redEffect(pixels) {
        // 影像資訊的分組是每四個一組 R、G、B、Alpha
        for (let i = 0; i < pixels.data.length; i+=4) {
          pixels.data[i + 0] = pixels.data[i + 0] + 200; // RED
          pixels.data[i + 1] = pixels.data[i + 1] - 50; // GREEN
          pixels.data[i + 2] = pixels.data[i + 2] * 0.5; // Blue
        }
        return pixels;
    }
</pre>
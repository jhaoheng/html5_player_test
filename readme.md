# readme

# how to use
1. `docker-compose up -d`
2. browser open : `localhost:8888`
3. browser open flash to support rtmp live

# troubleshooting

- rtmp 無法播放，請確認 browser support flash
- hls 無法播放，請確認 m3u8 與 ts 檔案的格式正確，resonse status code should be 200
- 切記，player 沒有問題，自己驗證過三次，還是忘記上面兩個需求

---


# hls playback
- hls.html
- use hls.js
- 替換掉 loadSource 即可
- 測試 m3u8 檔案播放
    - http://video-dev.github.io/hls.js/demo/
    - 若有錯誤，最下方會有錯誤提示

## m3u8 ex:
```
#EXTM3U
#EXT-X-VERSION:7
#EXT-X-ALLOW-CACHE:YES
#EXT-X-TARGETDURATION:17
#EXT-X-MEDIA-SEQUENCE:4
#EXT-X-START:TIME-OFFSET=0
#EXTINF:17, orbweb playback
1498033167521.ts
#EXTINF:17, orbweb playback
1498033184208.ts
#EXTINF:17, orbweb playback
1498033200891.ts
```

- #EXT-X-START:TIME-OFFSET=0 : 必須要 player 有支援解析

# rtmp live
> - 請開啟瀏覽器支援 flash，不然會出錯
> - chrome 設定方法 : 點選網址旁的 (i) -> 選擇網站設定。此方法會根據 chrome 版本更換有變

- rtmp.html
- use video.js
- 測試 利用 jwplayer
    - https://developer.jwplayer.com/tools/stream-tester/
    - http://demo.jwplayer.com/developer-tools/http-stream-tester/
        - 不處理 https / crossdomain 可用這個

## video.js issue 
播放後，影片會在左上角，與 player size 不符合
- bug fixed : https://github.com/videojs/video-js-swf/issues/55
    1. 下載 https://github.com/digitalStyx/video-js-swf/blob/master/bin-debug/VideoJS.swf
    2. 在 head 中加入
        ```
        <script>
          videojs.options.flash.swf = "VideoJS.swf";
        </script>
        ```
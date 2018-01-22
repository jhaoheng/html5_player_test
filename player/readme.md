# readme

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
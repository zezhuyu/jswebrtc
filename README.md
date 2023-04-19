# react-jswebrtc

react-jswebrtc 在原有 [JSWebrtc](https://github.com/kernelj/jswebrtc) 基础上改进，支持在react.js项目中引入.

原作者： [Derek Chan](https://github.com/kernelj)

原项目地址: https://github.com/kernelj/jswebrtc

项目地址: https://github.com/zezhuyu/jswebrtc
## 用法

安装: 

```bash
npm i react-jswebrtc
```

在React.js中使用: 

```html
<video id="webrtc_player"></video>
```

```javascript
import JSWebrtc from "react-jswebrtc"

if(JSWebrtc.isSupported()){
      var video = document.getElementById('webrtc_player');
      const player = new JSWebrtc.Player(url, {video: video});
      player.play()
}
```

在DPlayer中使用:

```javascript
import JSWebrtc from "react-jswebrtc"

const dp = new DPlayer({
    container: document.getElementById('dplayer'),
    video: {
        type: 'webrtc',
        customType: {
            'webrtc': function (video, player) {
                if(JSWebrtc.isSupported()){
                    new JSWebrtc.Player(url, {video: video});
                }
            }
        },
    },
})
```

参数 `url` 是一个 webrtc 开头的地址 (webrtc://...).

参数 `options` 支持下列的配置项: 

- `video` – 用于播放视频的 HTML Video 元素.
- `autoplay` - 是否自动播放. 默认 `false`.
- `onPlay(player)` – 播放后回调
- `onPause(player)` – 暂停后回调


## JSWebrtc.Player API

实例 `JSWebrtc.Player` 支持以下方法和属性:

- `.play()` – 开始
- `.pause()` – 暂停
- `.stop()` – 停止
- `.destroy()` – 停止播放并清理相关的播放资源.
- `.paused` – 只读, 是否暂停播放


## 构建

如何构建 min 文件:

```sh
npm i
./build.sh
```


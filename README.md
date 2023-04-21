# react-jswebrtc

Base on [JSWebrtc](https://github.com/kernelj/jswebrtc), Now react-jswebrtc supports import from React.js applications.

Author: [Derek Chan](https://github.com/kernelj)

Original Repo: https://github.com/kernelj/jswebrtc

Repo: https://github.com/zezhuyu/jswebrtc
## Usage

Install: 

```bash
npm i react-jswebrtc
```

Use in React.js: 

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

Use in DPlayer:

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

`url`: must start with webrtc://.

`options` parameters support: 

- `video` – for customized the html video element.
- `api` – for customized api url. by default it connects to `http://ip:1985/rtc/v1/play/`.
- `autoplay` - this will automatically mute and play the video after the player loads. `false` by default.
- `onPlay(player)` – callback function when video is played.
- `onPause(player)` – callback function when video is paused.


## JSWebrtc.Player API

`JSWebrtc.Player` instance support following operations:

- `.play()` – start.
- `.pause()` – pause.
- `.stop()` – stop.
- `.destroy()` – stop playing the video and free the resources.
- `.paused` – check if it is paused.


## Build

```sh
npm i
npm run build
```


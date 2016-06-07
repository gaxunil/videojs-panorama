# videojs-panorama

a plugin for videojs run a full 360 degree panorama video.

#### [DEMO HERE](http://yanwsh.github.io/videojs-panorama/)

## Table of Contents

<!-- START doctoc -->
<!-- END doctoc -->
## Installation

```sh
npm install --save videojs-panorama
```

or

#### [DOWNLOAD HERE](https://github.com/yanwsh/videojs-panorama/releases/download/0.0.5/videojs-panorama-0.0.5.zip)

## Integration with video.js 4 and 5

###1. If you don't have videoJs, add it's scripts and stylesheet to your page

```html
<!-- Video.js 4 -->
<link href="http://vjs.zencdn.net/4.12/video-js.css" rel="stylesheet">
<script src="http://vjs.zencdn.net/4.12/video.js"></script>
```
or

```html
<!-- Video.js 5 -->
<link href="http://vjs.zencdn.net/5.8/video-js.css" rel="stylesheet">
<script src="http://vjs.zencdn.net/5.8/video.js"></script>
```

###2. Add three.js after videoJs script
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r76/three.js"></script>
```
###3. Add the plugin stylesheet and script

```html
<!-- Common -->
<link href="//path/to/videojs-panorama.min.css" rel="stylesheet">
```
and the videojs version specific plugin, you can find it in **dist** folder
```html
<!-- Video.js 4 -->
<script src="//path/to/videojs-panorama.v4.min.js"></script>
```
or
```html
<!-- Video.js 5 -->
<script src="//path/to/videojs-panorama.v5.min.js"></script>
```
###4. setup videojs panorama plugin
```js
player.panorama({
    clickAndDrag: true,
    callback: function () {
      player.play();
    }
});
```

## Fisheye video support

In some cases, you get the video like below. 

![Image of fisheye poster](assets/poster-2.jpg)

You don't have to use tools to convert video to equirectangular video, you can use this plugin to play directly.

There are two cases for fisheye video.
One case is the camera took from top to bottom. You may need to restrict user only view the bottom half of the sphere
```js
player.panorama({
    maxLat: -10,
    initLat: -10,
    rotateX: -Math.PI,
});
```

Another case is the camera took from bottom to top.
```js
player.panorama({
    minLat: 10,
    initLat: 10,
    rotateX: 0,
});
    
```

## Options

### clickAndDrag
By default, video will be rotated when user rollover their mouse. If clickAndDrag set to true, video rotation will only happen on user drag and drop the video. `Defaults to false`

### callback
callback function fired when panorama video is ready.

### showNotice
A notice label show on the beginning of the video to notice user to drag the player to see whole video. If showNotice set to false, notice label will not be shown. `Defaults to true`

### NoticeMessage
Customize your own notice message. 

### autoHideNotice
How long the notice message should be shown. `Defaults to 3000`, indicate it will hide after 3000ms.

### initLat
initial lat for camera angle, `Defaults value is 0`, range between -90 to 90.

### initLon
initial lot for camera angle, `Defaults value is -180`, don't have range. 

### backToVerticalCenter
automatically back to vertical center when user inactive the video frame. `Defaults value depends on running platform, true on desktop, false on mobile`.

### returnStepLat
If backToVerticalCenter is set to true, you can customize the return back speed. `Defaults value is 0.5`. The larger the faster.

### backToHorizonCenter
automatically back to horizontal center when user inactive the video frame. Default value the same as `backToVerticalCenter`.

### returnStepLon
If backToHorizonCenter is set to true, you can customize the return back speed. `Defaults value is 2`.

### clickToToggle
click to toggle the video. If video is playing, it will be paused. If video is paused, it will be played. `Defaults to false`.

It's possible to customize the viewable zoom
### minLat
minimum Lat value for camera angle. `Defaults value is -90`.

### maxLat
max Lat value for camera angle. `Defaults value is 90`.

### videoType
This plugin can play two types of video, equirectangular and fisheye. `Defaults value is equirectangular`. 

## The property below only support fisheye video.

### rotateX
rotate video view by x axis. `Defaults value is 0`. Value should be radian.

### rotateY
rotate video view by y axis. `Defaults value is 0`. Value should be radian.

### rotateZ
rotate video view by z axis. `Defaults value is 0`. Value should be radian.


## browser support
IE 11, Edge 12, 13, chrome, firefox, safari, iphone ios 9, ipad ios 9, android 4.4 and above.

## License

Apache-2.0. Copyright (c) yanwsh@gmail.com


[videojs]: http://videojs.com/

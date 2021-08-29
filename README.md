# audioly

## Library for audio controls, visualization, waveform and trimming/cutting

### API (Usage)

**Instantiate the audioly class**
`const audioly = new Audioly(audio);`

**Sliders**

1. Fill slider

```
audioly.fillSlider(el, {
    options: {},
  });
```

- el: html element to be used as a slider (required)
- options:
  - thumb: boolean (optional)
  - thumbColor: string containing rgb or hex color (optional)
  - thumbWidth: string containing value in pixels. Should be "1", "2" etc, without px after the value(optional)
  - sliderRGBColor: Object with rgb color of the slider. Example, ```
    {
    r: "0",
    g: "0",
    b: "0",
    }
  ```(optional)

  ```

2. Cut slider

```
audioly.cutSlider(el, {
    options: {},
  });
```

_Same application as the fill slider with one additional option:_

- aud: an object with two keys {start, end}. The start key specifies the time in seconds where the audio should start playing, and the end key specifies the end of the audio play.

**Times**

1. getCurrentTime
   This will get the audio's current time in the format (mins:secs)
2. getDuration
   This will get the audio's full duration in the format (mins:secs)
3. currentPosition
   This will get the current audio position in seconds while you change the audio position

**Waveform**

```
drawWaveform(
  canvas,
  opt = {}
)
```

- canvas: The canvas html element (required)
- opt: options for the customization of the wave form. This has two properties, (optional)
  - color: The color of the waveform
  - background: The background color of the the canvas

**Icons**
`audIcons(name)`
This works hand in hand with fontawesome icons to get the icons for the audio controls. The name property can be any of the following:

- play: When the audio is paused
- pause: When the audio is playing
- mute: When the audio is not muted
- zero volume: When the audio's volume is 0
- unmute: When the audio is muted
- loop: When the audio is not looped
- back: The back button icon
- next: The next button icon

**Playing and pausing audio**

```
playPause(
   el,
   options = {
     playStr: "play",
     pauseStr: "pause",
   },
   styles = { on: null, off: null }
 )
```

- el: html element that acts as the playing and pausing button (required)
- options: an object with two keys {playStr,pauseStr} (optional)
  - playStr: Is the string value use when the audio is playing (works best with audIcons(name))
  - pauseStr: Is the string value use when the audio is paused (works best with audIcons(name))
- styles: an object with two keys {on,off} (optional)
  - on: The css styles for the specified html element when the audio is playing
  - off: The css styles for the specified html element when the audio is paused

**Backward and Forward**

1. `goBack(audList, { el: null, names: null })`
2. `goForward(audList, { el: null, names: null })`

- audList: An array containing list of audios to navigate (required)
  The following are optional but once the "el" is specified, the names will be required
- el: The element that displays the name of the playing audio (required)
- names: An array containing list of audios' names to navigate (required)

**Mute and Unmute**
`muteNunmute(el, muteStr, unmuteStr)`

- el: The html element acting as the mute button
- muteStr: Text/Icon to show when the audio is muted
- unmuteStr: Text/Icon to show when the audio is not muted

**Looping**

```
loopNunloop(
    el,
    options = {
      loopStr: "loop",
      unloopStr: "unloop",
    },
    styles = { on: null, off: null }
  )
```

_The application is the same as the one for playing and pausing the audio_

**Changing the volume**
`changeVolume(el)`
el: The html element acting as the volume slider (should be a range input element) (required).
_This works oninput and onchange events in javascript_

**Changing the audio position**
`changeAudPosition(el)`
el: The html element acting as the audio seek slider (should be a range input element) (required).
_This works oninput and onchange events in javascript_

**Updating the audio's time**
`updateAudTime(el)`
el: The html element acting as the audio seek slider (should be a range input element) (required).
_This works ontimeupdate event on audio in javascript_

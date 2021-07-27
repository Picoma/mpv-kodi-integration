This project aims at integrating mpv as much as possible with Kodi, while allowing high quality rendering of video files on 4K screens.

mpv is currently a much more powerful video player than the one integrated in Kodi (for example with the use of CNN-based shaders for scaling), but also more austere. 

This repository currently consists of the amalgamation of the following projects :
 - Mike Connelly's MPV configuration for 4K upscaling, described in ![this blog post](https://freetime.mikeconnelly.com/archives/5371) (config available ![here](https://github.com/classicjazz/mpv-config) ;
 - An adapted version of ![this OSC](mpv-osc-morden) for MPV, modified to include a clock on the screen's corner as well as a larger bar ;
 - Various scripts, available on ![MPV's wiki](https://github.com/mpv-player/mpv/wiki/User-Scripts), namely :
   - `oled-screensaver.lua`
   - `pause-indicator.lua`

# Installation
Simply clone this repository in `~/.config/mpv`.

# Usage
While playing a video, press `CTRL + 1` to enable Anime4K upscaling shaders (recommended only for anime, as it can lead to an oil-painty effect on action movies).
Press `CTRL + 2` to enable FSRCNNX upscaling.

### How to change the interface color
Initially red, the interface's color can be modified by changing the following line in `scripts/osd-kodi.lua` :

```lua
local osc_styles = {
    [...]
	SeekbarFg = '{\\blur1\\bord1\\1c&H######&}',
	[...]
    ClockColon = '{\\blur0\\bord0\\1c&H1C1CB7&\\3c&H######&\\fs72\\fnlato}',
    [...]
}
```
Replace `######` with the hex code of the color you want to use, **in BGR format, not RGB !**

# To do
 - Evaluate if it is useful to make a custom script linking mpv to Kodi's ![EventServer](https://kodi.wiki/view/EventServer), especially for setting Kodi's "Currently watching" state for a given film.
 - Enable Vulkan rendering (what are the required dependancies ?)
 - A Python utility for managing the configuration ?

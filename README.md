# Tetris GYM Cosmetics: Pride Edition and Darkmode
These two patches work on kirjava's [TetrisGYM v5 Tournament Edition](https://github.com/kirjavascript/TetrisGYM/releases/tag/v5-tournament), a highly featureful romhack for training and competing in NES Tetris.

Skip to:<br>
[Pride colors](#pride-level-colors)<br>
[Dark mode](#dark-mode)<br>
[Instructions and guide](#instructions--brief-dev-notes)

## Pride level colors
![The title logo for the pride colors hack](https://user-images.githubusercontent.com/65273893/236605727-b1e101b6-5a41-4705-b352-d242dcabd477.png)<br>
_<sup>The title logo in trans flag colors.</sup>_

This patch changes the level colors of the game to various pride flags. The level colors were originally chosen by 3RR0R404. It was adapted to Gym by deadmemelmao and yours truly, and you can download it in the releases page [here.](https://github.com/xnphls/gym-pride/releases/tag/v5TEpride)

### The colors

<img src="https://user-images.githubusercontent.com/65273893/236610315-ede7b58a-49b0-41c3-8abd-14ddf763cde0.png" width="800"><br>
_<sup>The new pride level colors. They loop every 10 levels.</sup>_

Each level's colors represent a different LGBT pride flag. We chose 10 of them, mainly focused on a selection that would make for nice, visible level colors. Some less common identities are on here, and some more common identities didn't make it on here at all because there just wasn't a way to make it look nice with the way the game draws blocks. The flags we chose are:

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Demiboy_Flag.svg/512px-Demiboy_Flag.svg.png?20180409095817" width="20" height="15"> **Level x0**  Demiboy <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Aromantic_Pride_Flag.svg/512px-Aromantic_Pride_Flag.svg.png?20180407203736" width="20" height="15"> **Level x1**  Aromantic <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Bisexual_Pride_Flag.svg/800px-Bisexual_Pride_Flag.svg.png?20220730224211" width="20" height="15"> **Level x2**  Bisexual <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Demigirl_Flag.svg/512px-Demigirl_Flag.svg.png?20190520173517" width="20" height="15"> **Level x3** Demigirl <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Nonbinary_flag.svg/1280px-Nonbinary_flag.svg.png" width="20" height="15"> **Level x4** Nonbinary <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/New_Gay_Pride_Flag.svg/1280px-New_Gay_Pride_Flag.svg.png" width="20" height="15"> **Level x5** Gay <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/12/Aroace_flag.svg/1280px-Aroace_flag.svg.png" width="20" height="15"> **Level x6** Aro-Ace <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Asexual_Pride_Flag.svg/512px-Asexual_Pride_Flag.svg.png?20180406211802" width="20" height="15"> **Level x7** Asexual <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/Transgender_Pride_flag.svg/512px-Transgender_Pride_flag.svg.png?20221008042421" width="20" height="15"> **Level x8** Transgender <br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Lesbian_pride_flag_2018.svg/1280px-Lesbian_pride_flag_2018.svg.png" width="20" height="15"> **Level x9** Lesbian <br>

## Dark mode
<img src="https://user-images.githubusercontent.com/65273893/236659261-9149ce36-123a-492d-85c5-88bbae76242a.png" width="800"><br>
_<sup>Dark mode is on the left; the regular GYM's look is on the right.</sup>_

This patch was originally conceived by doge_nestris. I've adapted it for use with Tournament Edition along with a few tweaks to the pixels, and it works seamlessly alongside the Pride hack. You can get the patch [here.](https://github.com/xnphls/gym-pride/releases/tag/v5TEdark) Personally, I find it hard to play the game without it.

## Instructions & brief dev notes
You can patch these using a utility such as [Rom Patcher JS.](https://www.marcrobledo.com/RomPatcher.js/) Make sure you're patching over an already-patched version of GYM Tournament Edition; it will not work on the default Tetris (USA) rom.

I'd also like to show you the process I used so you can mess around with the palettes and sprites yourself if you wish. It was a lot simpler than I feared going in; you do not need to know any assembly. Thanks to deadmemelmao for showing me how she does it.

### How the palettes were changed
The palette code was all changed in [Mesen,](https://www.mesen.ca/) which is the main emulator folks use for NEStris but also contains pretty powerful romhacking tools. For the sprite changes, I used [YY-CHR](https://www.romhacking.net/utilities/958/). There are other tools to do these things, too, but I don't know them and don't know how to use them. I barely know how to use _these._

For the Pride hack, it mainly just revolved around locating entries in the palette section of `PRG ROM`, which I messed around with in Mesen using `Debug -> Memory Tools`. To save any changes as a new rom, I had to open `Debug -> Debugger` and save as a new rom from that dialog. I also had `Debug -> PPU Viewer -> Palette Viewer` open to see the palettes active on the game screen I was on.

The level colors are located around `$20d3` in the `PRG ROM`. I found them with a search with `Ctrl+F`. They're formatted like `0f 30 16 12`, which are four different palette colors: `Black` for the background, `White` which will be the middle of T, O, and I's tiles, as well as the glints on the corners of the others, `Color 1` which paints the L and the Z, and `Color 2` which paints the J, the S, and the border of T, O, and I.

For instance, on level 18, the palette is `0f 30 16 12`, which looks like

<img src="https://user-images.githubusercontent.com/65273893/236662264-3213b989-9b97-4686-8992-32ef4a3a0e42.png" width="300">

Searching `0f301612` in `Memory Tools` found me the 18 colors in the ROM and allowed me to change it to the trans colors we chose, `0f302521`

<img src="https://user-images.githubusercontent.com/65273893/236662476-fdf0bdb0-80d7-4beb-8896-bd068a272c2c.png" width="300">

Here's the list of the palette entries for the levels and what I changed them to. Note that all the level colors use `30` for the white, except x2 which uses `25`, a light pink, because the bi flag doesn't have any white.

```
level    original        new             flag
x0:      0f 30 21 12     0f 30 00 21     demiboy
x1:      0f 30 29 1a     0f 30 00 1a     aromantic
x2:      0f 30 24 14     0f 25 11 14     bisexual
x3:      0f 30 2a 12     0f 30 00 25     demigirl
x4:      0f 30 2b 15     0f 30 28 14     nonbinary
x5:      0f 30 22 2b     0f 30 21 2b     gay
x6:      0f 30 00 16     0f 30 27 11     aro-ace
x7:      0f 30 05 13     0f 30 00 14     asexual
x8:      0f 30 16 12     0f 30 25 21     transgender
x9:      0f 30 27 16     0f 30 27 15     lesbian

title    0f 17 27 37     0f 21 30 25     transgender
```
There are many other color addresses that can be changed, too, but weren't for the sake of brevity. You can change the border colors, the menu colors, the rocket at the end of the game in Qual Mode (although that change I never quite got to work right)... with a bit of hunting and searching and peeking at the palette viewer, you can find what you're searching for.

### How the sprites were changed
The sprite work (which was used for the title logo of the pride rom and the tile changes of the darkmode rom) was done in YY-CHR, whose use is a little more straightforward if you've used image editing software before, but I'll at least show you a screenshot of the `CHR ROM` so you can see which things were altered. It's the spritesheet of the Pride rom with no darkmode. Note that these are false colors, as the palette is determined outside of the spritesheet.

**Legend:**

![#1589F0](https://placehold.co/15x15/ffff00/ffff00.png) _<sup>The background tiles that need to be deleted for dark mode.</sup>_<br>
![#1589F0](https://placehold.co/15x15/00ff00/00ff00.png) _<sup>The border tiles whose edges can be modified to look better against the background.</sup>_<br>
![#1589F0](https://placehold.co/15x15/00ffff/00ffff.png) _<sup>The title logo, pictured here already modified for the pride rom.</sup>_<br>
![#1589F0](https://placehold.co/15x15/ff00ff/ff00ff.png) _<sup>Nothing happened to these in either romhack, but these are the three piece sprites. Do with this information what you will.</sup>_

![chr notated](https://user-images.githubusercontent.com/65273893/236664306-b4fd88db-b9b6-4549-8f16-2c97915f7f0d.png)

##
We hope you enjoy the hacks. For any questions, I can be reached on Discord, Xenophilius#1814, or you can find me in the [CTM Discord server](https://ctm.gg/discord), along with quite a few people who are much better than me at this stuff. Come tell me if you made any cool hacks of your own!

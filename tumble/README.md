# Tilt Rivals artwork

Artwork for [Tilt Rivals](https://github.com/Zeref538/woodland-tumble), kept in this separate repository so the lab can download images without the Unity project. The game repository keeps its existing `woodland-tumble` address.

## Download on slow lab Wi-Fi

This downloads the current game artwork while leaving the larger source sheets and older assignments out of your working folder:

```sh
git clone --filter=blob:none --sparse https://github.com/Zeref538/Woodland-Scouts.git
cd Woodland-Scouts
git sparse-checkout set tumble/characters tumble/arena tumble/backgrounds tumble/menu tumble/ui tumble/vfx tumble/manifests
```

The selected PNG files total approximately 55 MB. Git also downloads repository information, so the network download size can differ.

For the entire artwork repository, including original sheets and earlier projects:

```sh
git clone https://github.com/Zeref538/Woodland-Scouts.git
cd Woodland-Scouts
```

## Update your existing copy

Run inside the `Woodland-Scouts` folder:

```sh
git fetch origin
git log --oneline HEAD..origin/main
git merge --ff-only origin/main
```

`fetch` checks for changes. `merge --ff-only` applies them without creating a merge commit. To check and update in one command:

```sh
git pull --ff-only
```

Save local edits before updating if Git reports that those files would be overwritten.

## Characters

| Character | Design | PNG frames | Actions |
|---|---|---:|---|
| Fern | Black-haired leaf scout | 140 | Walk, Jump, Hurt, Punch, Push, Knockout, Block, DoubleJump, Kick, Special, Dash, Backstep, Victory, Ultimate |
| Ember | Auburn-haired fire scout | 140 | Walk, Jump, Hurt, Punch, Push, Knockout, Block, DoubleJump, Kick, Special, Dash, Backstep, Victory, Ultimate |
| Luna | White-haired moon mage | 121 | Walk, Jump, Hurt, Knockout, Punch, Kick, Block, Special, Dash, Backstep, Victory, Ultimate |
| Bram | Stone-gauntlet woodland fighter | 121 | Walk, Jump, Hurt, Knockout, Punch, Kick, Block, Special, Dash, Backstep, Victory, Ultimate |

There are **522 individual character PNGs**. Animated action folders contain ten frames each; Luna and Bram also have one dedicated neutral Idle frame each. Each character has their own artwork. Luna and Bram's game animations use their own Jump poses for double jumping and their own Punch poses for the older Push compatibility state; those do not add extra PNG files.

Frames face right and run in filename order, `01.png` through `10.png`. Ordinary frames are 256x256. Special, Dash, Backstep, Victory and Ultimate frames are **384x256** so effects fit without shrinking the body.

Use a bottom-center foot pivot: `(128,24)` pixels on ordinary frames and `(192,24)` on wide frames. These coordinates count upward from the bottom. In Unity this is a custom normalized pivot of `(0.5,0.09375)` for both canvas widths. Scale uniformly; do not stretch width and height separately.

## Other artwork

| Folder | Contents |
|---|---|
| `arena/` | Four balancing planks and four sphere designs |
| `backgrounds/` | Forest, Moonlit Lake, Ember Grove, Skyward Ruins, and the older shared Scouts reference atlas |
| `menu/` | Illustrated title backdrop and world atlas |
| `ui/` | Scout plate, header shade, interface surfaces, and native controller circles/shapes |
| `vfx/` | Sixteen earlier slash frames plus 48 new character-specific combo effect frames |
| `sources/` | Forty-nine original source sheets, preserved without image changes |
| `manifests/` | Frame counts, source rectangles, dimensions and image hashes |

The complete `tumble/` artwork contains **701 PNGs**, including the original source sheets. It contains no game scripts, Unity project files or import settings.

## Checks

All 701 PNGs decode successfully. The character manifest lists the previous 360 frames with their dimensions, visible bounds and SHA-256 image hashes.

The new roster pass adds 200 frames across twenty action folders. Each folder contains ten distinct images. All 200 have at least four transparent pixels around their visible artwork. Transparent row gutters and connected silhouettes were used for slicing because the generated sheets do not have perfectly even cells.

`manifests/ROSTER-ART-v6.json` records each new frame's source rectangle, alignment, scale and source-sheet hash. Two Bram knockout poses and one unused anticipation pose come from a second original Bram sheet; the manifest identifies those sources. These are asset checks, not a claim that a separate artwork download is a running game.

The compact HUD update adds four pixel-art action covers and a VS emblem. Actions show their controller symbol or keyboard key as a small overlay; the native diamond connector is also included. Original sheets and extraction hashes are recorded in `manifests/HUD-ART-v6.1.json`.

Each scout now has four separate action covers under `ui/Actions/{Fern,Ember,Luna,Bram}/`. Fern uses roots and leaves, Ember flames, Luna moonlight and frost, and Bram stone gauntlets and ground fissures. All sixteen images have different decoded image hashes. The root-level four action icons remain legacy assets; the game uses the character folders.

## v7 action artwork

Four new actions per character add 160 distinct frames: Dash, Backstep, Victory and Ultimate. They use transparent 384x256 canvases with a bottom foot pivot 24 pixels above the lower edge. A single scale per source keeps body size consistent without stretching effects. All 160 decode and every action has ten distinct images with at least four transparent pixels around the artwork. Luna Ultimate was regenerated to replace a merged pose and an effect-only tile; its neutral body is approximately 197 pixels tall, compared with the nominal 200-pixel body calibration.

`manifests/ROSTER-ART-v7.json` records the new frames and source hashes. Original action sheets remain under `sources/v7/`.

The v7 arena update adds eight dedicated PVP sprites under `arena/PVP/{Forest,Moonlit,Ember,Skyward}/`: a Base and Ledge for each theme. Their opaque top profile is aligned near local Y +0.04 when displayed at widths 14 and 4.2 respectively, using uniform scaling. Four new Jump action covers are under `ui/Actions/{Fern,Ember,Luna,Bram}/Jump.png`. Platform and cover source sheets and hashes are listed in `manifests/ARENA-ACTION-ART-v7.json`.

The 48 combo-effect frames live under `vfx/combo/{character}/{Hit,Finisher}/`, six frames per sequence. Each transparent PNG is 256x256 and uses a 64-pixel design grid for crisp pixels. These effects use a centered pivot, unlike the characters' foot pivot. `manifests/COMBO-ART-v7.json` records output hashes. The runtime selection contains 652 PNGs totaling 55,106,332 bytes; the larger original sheets are optional.

## v8 neutral idle corrections

Luna and Bram now have dedicated planted standing poses in `characters/{Luna,Bram}/Idle/01.png`, so portraits and Idle clips no longer need a running Walk frame. Both use transparent 256x256 canvases, a 200px subject height, feet baseline232, and the same custom feet pivot `(0.5,0.09375)`. Each was uniformly resized with nearest neighbour; no width or height stretching was used.

The two inspected original sources remain under `sources/`. `manifests/ROSTER-v8.json` records hashes and crop rectangles, plus 320 existing frame bounds labelled as including effects. The original Punch and Kick sprites already differ by character; generic green runtime overlays must be corrected in game code.

## v8.1 guard icons

Four chunky pixel shields replace character portraits on the guard buttons: leaf, phoenix, moon and stone. Each transparent icon is 256x256 with uniform nearest-neighbor sizing. The original atlas is preserved in `sources/Guard-Atlas-v8.1-source.png`; `manifests/GUARD-ART-v8.1.json` records output hashes.

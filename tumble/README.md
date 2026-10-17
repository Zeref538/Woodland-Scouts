# Wildwood Rivals artwork

Artwork for [Wildwood Rivals](https://github.com/Zeref538/woodland-tumble), kept in this separate repository so the lab can download images without the Unity project. The game repository keeps its existing `woodland-tumble` address.

## Download on slow lab Wi-Fi

This downloads the current game artwork while leaving the larger source sheets and older assignments out of your working folder:

```sh
git clone --filter=blob:none --sparse https://github.com/Zeref538/Woodland-Scouts.git
cd Woodland-Scouts
git sparse-checkout set tumble/characters tumble/arena tumble/backgrounds tumble/menu tumble/ui tumble/vfx tumble/manifests
```

The selected PNG files total approximately 39 MB. Git also downloads repository information, so the network download size can differ.

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
| Fern | Black-haired leaf scout | 100 | Walk, Jump, Hurt, Punch, Push, Knockout, Block, DoubleJump, Kick, Special |
| Ember | Auburn-haired fire scout | 100 | Walk, Jump, Hurt, Punch, Push, Knockout, Block, DoubleJump, Kick, Special |
| Luna | White-haired moon mage | 80 | Walk, Jump, Hurt, Knockout, Punch, Kick, Block, Special |
| Bram | Stone-gauntlet woodland fighter | 80 | Walk, Jump, Hurt, Knockout, Punch, Kick, Block, Special |

There are **360 individual character PNGs**, with ten frames per action folder. Each character has their own artwork. Luna and Bram's game animations use their own Jump poses for double jumping and their own Punch poses for the older Push compatibility state; those do not add extra PNG files.

Frames face right and run in filename order, `01.png` through `10.png`. Ordinary frames are 256x256. Each character's Special frames are **384x256** so vines, fire, moon magic and stone effects fit without shrinking the body.

Use a bottom-center foot pivot: `(128,24)` pixels on ordinary frames and `(192,24)` on Special frames. These coordinates count upward from the bottom. In Unity this is a custom normalized pivot of `(0.5,0.09375)` for both canvas widths. Scale uniformly; do not stretch width and height separately.

## Other artwork

| Folder | Contents |
|---|---|
| `arena/` | Four balancing planks and four sphere designs |
| `backgrounds/` | Forest, Moonlit Lake, Ember Grove, Skyward Ruins, and the older shared Scouts reference atlas |
| `menu/` | Illustrated title backdrop and world atlas |
| `ui/` | Scout plate, header shade, interface surfaces, and native controller circles/shapes |
| `vfx/` | Eight Fern and eight Ember slash frames |
| `sources/` | Nineteen original source sheets, preserved without image changes |
| `manifests/` | Frame counts, source rectangles, dimensions and image hashes |

The complete `tumble/` artwork contains **423 PNGs**, including the original source sheets. It contains no game scripts, Unity project files or import settings.

## Checks

All 423 PNGs decode successfully. The character manifest lists all 360 frames with their dimensions, visible bounds and SHA-256 image hashes.

The new roster pass adds 200 frames across twenty action folders. Each folder contains ten distinct images. All 200 have at least four transparent pixels around their visible artwork. Transparent row gutters and connected silhouettes were used for slicing because the generated sheets do not have perfectly even cells.

`manifests/ROSTER-ART-v6.json` records each new frame's source rectangle, alignment, scale and source-sheet hash. Two Bram knockout poses and one unused anticipation pose come from a second original Bram sheet; the manifest identifies those sources. These are asset checks, not a claim that a separate artwork download is a running game.

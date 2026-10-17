# Woodland Tumble artwork

Artwork for [Woodland Tumble](https://github.com/Zeref538/woodland-tumble), kept separately so you can download images without the Unity project.

## Clone

Open Terminal on Mac or PowerShell on Windows:

```sh
git clone https://github.com/Zeref538/Woodland-Scouts.git
cd Woodland-Scouts
```

The artwork for this game is in `tumble/`. Older artwork remains in the other folders.

## Get the latest changes

Run these inside the cloned `Woodland-Scouts` folder:

```sh
git fetch origin
git log --oneline HEAD..origin/main
git merge --ff-only origin/main
```

`fetch` downloads the changes for inspection. `merge --ff-only` updates your files without creating a merge commit. To download and update in one command instead:

```sh
git pull --ff-only
```

If Git says local edits would be overwritten, save those edits before updating.

## Folders

| Folder | Contents |
|---|---|
| `characters/Fern/` | Green scout: Walk, Jump, Hurt, Punch, Push, Knockout, Block and DoubleJump |
| `characters/Ember/` | Amber scout: Walk, Jump, Hurt, Punch, Push, Knockout, Block and DoubleJump |
| `vfx/Fern/` and `vfx/Ember/` | Eight green and eight amber effect frames, each 256x256 |
| `arena/` | Three plank designs and three balancing spheres |
| `ui/` | Transparent 410x146 scout HUD plate with stepped corners and a thin rim |
| `backgrounds/` | Forest, Moonlit Lake and Ember Grove backgrounds |

The character pack contains 160 individual transparent 256x256 PNG frames, ten per action for each character. This includes 40 new Block and DoubleJump frames. Every frame decodes successfully, and the new frames leave at least four transparent pixels at each canvas edge. This folder contains artwork only, with no game scripts or Unity import settings.


The effect pack adds 16 individual transparent 256x256 PNGs, eight per element. Together with the 160 character frames, there are 176 character and VFX frames. The three backgrounds and six arena images are unchanged.


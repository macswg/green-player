# Marker Player

A browser video player for recorded takes, with a searchable list of the markers
logged during recording. Click a marker to jump to it.

**Open it:** https://macswg.github.io/marker-player/

Works in Chrome, Edge, Safari and Firefox on Mac and PC. No install, no account.

## Your footage stays on your computer

The site is a single static page. When you open a folder, the browser reads the
files directly from your disk; nothing is uploaded to GitHub or anywhere else.
To use it offline, download `index.html` and double-click it.

## Use

1. Click **Open folder…** and pick the folder of recordings (or drag it onto the window).
   If the browser asks to "upload" the folder, that only lets the page read it locally.
2. Pick a take on the left. Its markers are listed on the right.
3. Click a marker to jump to it, double-click to jump and play.

Each video is paired with the marker file beside it that has the same name:

```
Take_1.5.mp4
Take_1.5.markers.csv
```

Keep the two together when copying or sharing takes. Videos without a marker
file still play.

## Search

| Search | Shows |
| --- | --- |
| `verse` | markers containing "verse" in any column |
| `verse*2` | `*` is a wildcard: "Verse 2", "verse 1 into 2" |
| `-intro` | hides markers containing "intro" |
| `"verse 2"` | quotes keep spaces; also `-"pre roll"` |
| `chorus -mark` | all words must match |

Not case-sensitive. The type buttons under the search box filter too.

## Keys

| Key | Does |
| --- | --- |
| Space | play / pause |
| ↑ ↓ or [ ] | previous / next marker |
| ← → | back / forward 5 s (Shift: one frame) |
| P | play from the current marker to the next one |
| L | loop that section |
| / | search markers |

## Marker file

A CSV with a header row. `time` (seconds from the start of the video) is the only
required column; the player also uses `type`, `label`, `transport`, `track`,
`section`, `cue`, `d3_timecode` and `clock`. A `stop` row holding the take's
length by the recording clock lets the player rescale marker times if the video
came out shorter or longer.

```
time,type,label,transport,track,section,cue,d3_timecode,track_position,clock
0.000,start,120_song / Intro,show_b,120_song,Intro,CUE 012.000.000,00:00:03;01,00:00:03;01,21:14:05.120
12.480,mark,camera 3 glitch,show_b,120_song,Intro,CUE 012.000.000,00:00:15;15,00:00:15;15,21:14:17.600
95.002,stop,REC stop,,,,,,,21:15:40.122
```

H.264 `.mp4` plays everywhere. ProRes `.mov` plays only in Safari on a Mac.

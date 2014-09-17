# Unix Screen Cheatsheet

## Basic commands

| Task | Command|
| --- |:---|
| Start a new screen session with session name  | screen -S [name] |
| List running sessions/screens  | screen -ls |
| attach to a running session | screen -x |
| attach to session with name  | screen -r [name] |

## Help

```
^a ?
```

## Multi user mode

```
^a:multiuser on
```

## Getting Out

| Task | Command |
| --- |:---|
|detach  | `^a d` |
|detach and logout (quick exit)  | `^a D D` |
|exit screen | `^a : quit` or exit all of the programs in screen. |


## Window Management

| Task | Command |
| --- |:---|
|create new window  | `^a c`|
|change to last-visited active window  |  `^a ^a` (commonly used to flip-flop between two windows)|
|change to window by number | `^a <number>` (only for windows 0 to 9)|
|change to window by number or name | `^a ' <number or title>`|
|change to next window in list  | `^a n` or `^a <space>`|
|change to previous window in list |  `^a p` or `^a <backspace>`|
|see window list | `^a "` (allows you to select a window to change to)|
|show window bar | `^a w` (if you don't have window bar)|
|kill current window | `^a k` (not recommended)|
|kill all windows   | `^a \` (not recommended)|
| rename current window  | `^a A`|

## Split Screen

| Task | Command |
| --- |:---|
| split display horizontally  | `^a S` |
| split display vertically    | `^a` or `^a V` (for the vanilla vertical screen patch) |
| jump to next display region | `^a tab` |
| remove current region   | `^a X` |
| remove all regions but the current one  | `^a Q` |


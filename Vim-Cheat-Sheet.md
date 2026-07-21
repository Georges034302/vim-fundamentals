# Vim Cheat Sheet

Press `Esc` before using Normal-mode commands. Press `Enter` after commands beginning with `:`, `/`, or `?`.

## 1. Vim Modes

| Command | Use | Example |
|---|---|---|
| `Esc` | Enter **Normal mode** (often called command mode) | Press `Esc`, then use `dd` |
| `i` | Enter Insert mode before the cursor | `iHello` |
| `a` | Enter Insert mode after the cursor | `a!` |
| `o` | Open a new line below and enter Insert mode | `oNew line` |
| `O` | Open a new line above and enter Insert mode | `ONew heading` |
| `:` | Enter Command-line mode | `:w` saves the file |
| `v` / `V` | Select characters / whole lines | `Vj` selects two lines |

## 2. Navigation and Line Numbers

| Command | Use | Example |
|---|---|---|
| `h` `j` `k` `l` | Move left, down, up, right | `5j` moves down five lines |
| `w` / `b` | Move to next / previous word | `3w` moves forward three words |
| `0` / `^` | Move to column 1 / first non-blank character | `^` jumps to the first text |
| `$` | Move to the end of the line | `d$` deletes to line end |
| `gg` / `G` | Go to the first / last line | `G` jumps to the end of the file |
| `25G` | Go to a specific line | `25G` jumps to line 25 |
| `:25` | Go to a specific line | `:25` jumps to line 25 |
| `Ctrl-d` / `Ctrl-u` | Move down / up half a screen | Press `Ctrl-d` to scroll down |
| `:set number` | Show absolute line numbers | `:set number` |
| `:set nonumber` | Hide line numbers | `:set nonumber` |
| `:set relativenumber` | Show relative line numbers | `:set relativenumber` |

To show line numbers whenever Vim starts, add `set number` to `~/.vimrc`.

## 3. Editing

| Command | Use | Example |
|---|---|---|
| `x` | Delete the character under the cursor | `3x` deletes three characters |
| `dw` | Delete from the cursor to the next word | `2dw` deletes two words |
| `dd` | Delete the current line | `3dd` deletes three lines |
| `D` | Delete from the cursor to the end of the line | `D` |
| `r<char>` | Replace one character | `ra` replaces the character with `a` |
| `cw` | Change from the cursor to the end of the word | `cwserver` |
| `u` | Undo the last change | `u` |
| `Ctrl-r` | Redo an undone change | Press `Ctrl-r` |
| `.` | Repeat the last change | Delete a word with `dw`, then press `.` |

## 4. Search and Replace

| Command | Use | Example |
|---|---|---|
| `/text` | Search forward | `/server` |
| `?text` | Search backward | `?server` |
| `n` / `N` | Go to the next / previous match | Search with `/error`, then press `n` |
| `*` | Search forward for the word under the cursor | Place the cursor on `port`, then press `*` |
| `:s/old/new/` | Replace the first match on the current line | `:s/http/https/` |
| `:s/old/new/g` | Replace every match on the current line | `:s/foo/bar/g` |
| `:%s/old/new/g` | Replace every match in the file | `:%s/foo/bar/g` |
| `:%s/old/new/gc` | Replace throughout the file with confirmation | `:%s/foo/bar/gc` |
| `:5,10s/old/new/g` | Replace within a line range | `:5,10s/dev/prod/g` |

## 5. Copy, Cut, and Paste

In Vim, **yank** means copy and **delete** also acts as cut.

| Command | Use | Example |
|---|---|---|
| `yy` | Copy the current line | `3yy` copies three lines |
| `yw` | Copy from the cursor to the next word | `2yw` copies two words |
| `dd` | Cut the current line | `2dd` cuts two lines |
| `dw` | Cut from the cursor to the next word | `dw` |
| `p` | Paste after the cursor or below the line | `yy`, move, then `p` |
| `P` | Paste before the cursor or above the line | `dd`, move, then `P` |
| `V` then `y` | Select and copy whole lines | `V2jy` copies three lines |
| `V` then `d` | Select and cut whole lines | `Vjd` cuts two lines |

## 6. Combined and Complex Commands

| Command | Use | Example |
|---|---|---|
| `J` | Join the current line with the next, adding normal spacing | Place the cursor on line 4 and press `J` |
| `gJ` | Join lines without adding or removing spaces | Place the cursor on line 4 and press `gJ` |
| `3J` | Join the current line and the next two lines | `3J` |
| `:5,8join` | Join a specified line range | `:5,8join` |
| `d3w` | Combine an operator, count, and motion | Delete three words with `d3w` |
| `ciw` | Change the entire word under the cursor | Place the cursor inside a word and use `ciw` |
| `di"` | Delete text inside double quotes | In `"hello"`, use `di"` |
| `>>` / `<<` | Indent / unindent the current line | `3>>` indents three lines |
| `=G` | Re-indent from the current line to the end | Use `gg=G` to re-indent the whole file |

## 7. Save and Exit

| Command | Use | Example |
|---|---|---|
| `:w` | Save changes | `:w` |
| `:w newfile.txt` | Save to another filename | `:w backup.txt` |
| `:q` | Quit if there are no unsaved changes | `:q` |
| `:wq` | Save and quit | `:wq` |
| `:x` | Save only if changed, then quit | `:x` |
| `ZZ` | Save and quit from Normal mode | Press `Esc`, then `ZZ` |
| `:q!` | Quit and discard unsaved changes | `:q!` |

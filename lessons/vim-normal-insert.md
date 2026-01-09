# Vim Fundamentals – Normal & Insert Mode
---

## What Is Vim?

### Definition & Explanation

Vim is a **modal text editor**, meaning the same key behaves differently depending on the current mode.

Vim operates primarily in two modes:

- **Normal mode** – keys are interpreted as **commands**
- **Insert mode** – keys are interpreted as **text characters**

Vim **always starts in Normal mode**.

> **Rule:** When confused, press `Esc` to return to Normal mode.

### Example

```bash
vim demo.txt
```

1. Vim opens in **Normal mode**
2. Press `i` → switch to Insert mode
3. Type text
4. Press `Esc` → return to Normal mode

---

## Mode Switching

### Definition & Explanation

Mode-switching commands determine **where and how text insertion begins**.
All insertion commands switch from **Normal mode** to **Insert mode**.

### Commands

```text
i   → insert before cursor
a   → insert after cursor
I   → insert at start of line
A   → insert at end of line
Esc → return to Normal mode
```

### Examples

```vim
iHello
Esc
```

```vim
A # comment
Esc
```

---

## Moving the Cursor (Normal Mode)

### Definition & Explanation

Movement commands reposition the cursor without modifying text.
They are often combined with other operations using the pattern:

**operator + movement**

### Commands

```text
0    → start of line
$    → end of line
w    → next word
b    → previous word
gg   → top of file
G    → bottom of file
:n   → jump to line n
```

### Examples

```vim
0
$
```

```vim
:42
```

---

## Inserting Text (Insert Mode)

### Definition & Explanation

Insert commands control where typing begins relative to the cursor.
While in Insert mode, all keys insert characters until `Esc` is pressed.

### Commands

```text
i → insert before cursor
a → insert after cursor
A → insert at end of line
```

### Examples

```vim
iText
Esc
```

```vim
aMore
Esc
```

```vim
A end of line
Esc
```

---

## Cutting Text (Delete = Cut)

### Definition & Explanation

In Vim, deleting text also **cuts** it.
Cut text is stored automatically and can be pasted later.

### Command

```text
d → delete (cut)
```

### Examples

```vim
dw   → cut word
dd   → cut line
d$   → cut to end of line
```

---

## Copying Text (Yanking)

### Definition & Explanation

Copying text in Vim is called **yanking**.
Yanked text is stored but does not modify the file.

### Command

```text
y → yank (copy)
```

### Examples

```vim
yw   → copy word
yy   → copy line
y$   → copy to end of line
```

---

## Pasting Text

### Definition & Explanation

Pasting inserts the most recently cut or copied text.
Placement depends on the paste command used.

### Commands

```text
p → paste after cursor
P → paste before cursor
```

### Examples

```vim
p
```

```vim
P
```

---

## Copy + Paste (Duplicating Text)

### Definition & Explanation

Copying followed by pasting duplicates text.

### Examples

```vim
yy
p
```

```vim
3yy
p
```

---

## Cut + Paste (Moving Text)

### Definition & Explanation

Vim has no dedicated move command.
Moving text is performed using **cut + paste**.

### Examples

```vim
dd
p
```

```vim
dd
k
P
```

---

## Searching Text

### Definition & Explanation

Searching allows forward pattern matching within a file.
Matches are navigated without leaving Normal mode.

### Commands

```text
/ → search
n → next match
N → previous match
```

### Examples

```vim
/error
n
```

```vim
/\<user\>
```

---

## Search and Replace

### Definition & Explanation

Search and replace uses command-line mode to substitute text.
The `%` symbol applies the substitution to the entire file.

### Command

```text
:s → substitute
```

### Examples

```vim
:%s/foo/bar/g
```

```vim
:%s/http/https/g
```

---

## Yanking and Marking

### Marking – Definition & Explanation

Marks store named positions in a file.
They allow fast navigation and safe manipulation of large blocks of text.

### Commands

```text
m → set mark
' → jump to mark
```

### Examples

```vim
ma
```

```vim
'a
```

### Yank Using Marks

```vim
ma
```
(move cursor)
```vim
y'a
```

### Cut / Move Using Marks

```vim
ma
```
(move cursor)
```vim
d'a
p
```

---

## Other Useful Commands

### Line Numbers

```vim
:set number
:set nonumber
```

### Join Lines

```vim
J
```

### Undo / Redo

```vim
u
Ctrl+r
```

---

## Key Takeaways

- Normal mode performs actions
- Insert mode types text
- Delete = cut
- Yank = copy
- Paste controls placement
- Marks define scope
- `Esc` always saves you

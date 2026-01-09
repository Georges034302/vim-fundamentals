# Exercise 1 – Solution (Movement Only)

**File:** `demo.txt`  
**Mode:** Normal mode only  
**Text modification:** None

---

## Step 1 — Open the file

```bash
vim demo.txt
```

---

## Step 2 — Go to the first line of the file

```vim
gg
```

**Result:** Cursor moves to line 1.

---

## Step 3 — Go to the last line of the file

```vim
G
```

**Result:** Cursor moves to the last line of the file.

---

## Step 4 — Go to the line containing `START`

```vim
/START
```

**Result:** Cursor moves to the line containing `START`.

---

## Step 5 — Go to the line containing `PASTE`

```vim
/PASTE
```

**Result:** Cursor moves to the line containing `PASTE`.

---

## Step 6 — Quit without saving

```vim
:q
```

---

## Completion Check

- Cursor successfully moved using `gg`, `G`, and search
- No text was modified

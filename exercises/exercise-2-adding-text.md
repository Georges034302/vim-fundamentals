# Exercise 2 – Solution (Adding Text)

**File:** `demo.txt`  
**Modes used:** Normal and Insert  

---

## Step 1 — Open the file

```bash
vim demo.txt
```

---

## Step 2 — Go to the line starting with `TITLE`

```vim
/TITLE
```

---

## Step 3 — Append text at the end of the line

```vim
A (BASIC PRACTICE)
```

---

## Step 4 — Return to Normal mode

```vim
Esc
```

---

## Step 5 — Go to the line starting with `PASTE`

```vim
/PASTE
```

---

## Step 6 — Open a new line below

```vim
o
```

---

## Step 7 — Insert text

```text
This line was added using Vim.
```

---

## Step 8 — Return to Normal mode

```vim
Esc
```

---

## Step 9 — Save and quit

```vim
:wq
```

---

## Completion Check

- `(BASIC PRACTICE)` added to TITLE line
- New line added below `PASTE`
- File saved successfully

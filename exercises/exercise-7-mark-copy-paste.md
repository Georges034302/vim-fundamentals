# Exercise 7 – Mark a Section and Copy–Paste It (Advanced)

**File:** `demo.txt`  
**Skills tested:** marking, copying, pasting, search  
**Modes allowed:** Normal and Insert  
**Not allowed:** Visual mode, macros

---

## Exercise Objective

The goal of this exercise is to:

- Mark the beginning of a multi-line section
- Copy the entire section using the mark
- Paste the copied section after a specific line
- Ensure the original section remains unchanged

This exercise focuses on **precision editing using marks**.

---

## Student Task

### Task 1 — Locate and mark the start of the section

1. Find the line starting with:
   ```
   START
   ```
2. Place a mark named `a` on this line.

---

### Task 2 — Locate the end of the section

1. Find the line starting with:
   ```
   END
   ```
2. Ensure the cursor is positioned on this line.

---

### Task 3 — Copy the section using the mark

Copy the entire block of text:
- starting from the line marked `a`
- ending at the current cursor position (`END`)

---

### Task 4 — Locate the destination

1. Find the line starting with:
   ```
   PASTE
   ```
2. Position the cursor on this line.

---

### Task 5 — Paste the copied section

Paste the copied section **after** the `PASTE` line.

---

### Task 6 — Save and quit

Save the file and exit Vim.

---

## Solution – Step-by-Step (Strict)

### Step 1 — Open the file

```bash
vim demo.txt
```

Vim opens in **Normal mode**.

---

### Step 2 — Search for the START line

```vim
/START
```

**Result:** Cursor moves to the line:
```
START
```

---

### Step 3 — Mark the START line

```vim
ma
```

**Result:** The START line is saved as mark `a`.

---

### Step 4 — Search for the END line

```vim
/END
```

**Result:** Cursor moves to the line:
```
END
```

---

### Step 5 — Copy the block using the mark

```vim
y'a
```

**Explanation:**
- `y` → yank (copy)
- `'a` → from the current cursor position back to mark `a`

**Result:** The entire START…END block is copied.

---

### Step 6 — Search for the PASTE line

```vim
/PASTE
```

**Result:** Cursor moves to the line:
```
PASTE
```

---

### Step 7 — Paste the copied block after PASTE

```vim
p
```

**Result:** The copied section appears immediately after the `PASTE` line.

---

### Step 8 — Save the file

```vim
:w
```

---

### Step 9 — Quit Vim

```vim
:q
```

(or in one step)

```vim
:wq
```

---

## Completion Check

The exercise is correct if:

- The section from `START` to `END` appears **twice**
- The second copy appears immediately after the `PASTE` line
- The original section remains unchanged
- No other lines are modified
- The file is saved successfully

---

## Commands Tested

```text
/START    → search
ma        → mark position
/END      → search
y'a       → copy using mark
/PASTE    → search
p         → paste after cursor
:w        → save
:q        → quit
```

---

## Key Learning Outcome

Marks allow you to:
- Define stable boundaries
- Copy or move large sections safely
- Perform non-linear edits with confidence

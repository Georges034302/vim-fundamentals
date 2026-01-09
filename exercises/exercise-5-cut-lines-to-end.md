# Exercise 5 – Cut by Line Numbers and Paste at End of File

## Exercise Objective

The goal of this exercise is to:

- Cut the block of text **from line 5 to line 9**
- Paste that block **after the last line of the file**

This exercise reinforces:
- Line-based navigation
- Range-based cutting
- Pasting at the end of a file

All commands are performed in **Normal mode**.

---

## Initial File Context

The exercise assumes the file `demo.txt` contains multiple lines and that:

- Line numbers are visible or known
- Lines **5 to 9** form a contiguous block of text to be moved

---

## Step-by-Step Solution

### 1. Open the file

```bash
vim exercises/demo.txt
```

Vim opens in **Normal mode**.

---

### 2. (Optional) Enable line numbers

This step helps verify line positions.

```vim
:set number
```

---

### 3. Jump to line 5

```vim
:5
```

Ensure the cursor is positioned on **line 5**.

---

### 4. Cut lines 5 to 9

```vim
d5
```

Explanation:
- `d` → delete (cut)
- `5` → delete this line and the **next 4 lines**

This cuts **lines 5 through 9** and stores them in Vim’s register.

---

### 5. Jump to the end of the file

```vim
G
```

The cursor is now on the **last line** of the file.

---

### 6. Paste after the last line

```vim
p
```

- `p` pastes **after** the current line
- Since the cursor is on the last line, the block is appended to the file

---

### 7. (Optional) Disable line numbers

```vim
:set nonumber
```

---

### 8. Save and quit

```vim
:wq
```

---

## Final File State

After completing the exercise:

- Lines originally at **5–9** now appear at the **end of the file**
- All other lines remain in their original order

---

## Key Concepts Reinforced

- `:n` jumps directly to a line
- `d<number>` cuts multiple lines starting at the cursor
- `G` moves to the end of the file
- `p` pastes content after the cursor
- Line-based operations are fast and precise in Vim

---

## Common Mistakes

- Forgetting to position the cursor on line 5 before deleting
- Using `P` instead of `p`, which pastes before the last line
- Forgetting to return to Normal mode before issuing commands

---

## Completion Criteria

The exercise is correct if:

- Lines 5–9 appear at the end of the file
- No additional lines are removed
- File structure remains otherwise unchanged

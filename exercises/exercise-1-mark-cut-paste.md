# Exercise Solution – Mark, Cut, and Paste in Vim

## Exercise Objective

The goal of this exercise is to:

- Mark the **beginning of a section** starting with the word `START`
- Include all lines up to and including the line starting with `END`
- Cut (delete) the marked section
- Paste the section **after the line starting with `PASTE`**

This solution uses **Normal mode only** for all operations.

---

## Initial File Structure (Before)

```text
PASTE
This line is where you must paste the block (after this line).

Some unrelated text line 1
Some unrelated text line 2

START
Line 1: This is inside the block.
Line 2: Keep all these lines together.
Line 3: You will cut this section.
Line 4: And paste it after the PASTE line.
END
Some text after END that should not move.
```

---

## Step-by-Step Solution

### 1. Open the file

```bash
vim exercises/demo.txt
```

Vim opens in **Normal mode**.

---

### 2. Search for the START line

```vim
/START
```

Ensure the cursor is positioned on the line that begins with `START`.

---

### 3. Mark the beginning of the block

```vim
ma
```

- `m` sets a mark
- `a` names the mark

The start of the block is now saved as mark `a`.

---

### 4. Search for the END line

```vim
/END
```

Ensure the cursor is on the line that begins with `END`.

---

### 5. Cut the block using the mark

```vim
d'a
```

Explanation:
- `d` → delete (cut)
- `'a` → from the current cursor position back to mark `a`

This deletes (cuts) **all lines from `START` through `END`**, storing them in Vim’s register.

---

### 6. Search for the PASTE line

```vim
/PASTE
```

Position the cursor on the line that begins with `PASTE`.

---

### 7. Paste the block after the PASTE line

```vim
p
```

- `p` pastes **after** the current line

The cut block is inserted immediately after the `PASTE` line.

---

### 8. Save and quit

```vim
:wq
```

---

## Final File Structure (After)

```text
PASTE
This line is where you must paste the block (after this line).

START
Line 1: This is inside the block.
Line 2: Keep all these lines together.
Line 3: You will cut this section.
Line 4: And paste it after the PASTE line.
END

Some unrelated text line 1
Some unrelated text line 2

Some text after END that should not move.
```

---

## Key Concepts Reinforced

- Marks define **range boundaries**
- `d` deletes and cuts text
- `p` controls where pasted text appears
- Complex edits can be performed safely using **search + mark + operator**

---

## Common Mistakes

- Forgetting to place the cursor on the `END` line before deleting
- Using `p` instead of `P` (or vice versa)
- Not returning to Normal mode before running commands

---

## Completion Criteria

The exercise is correct if:

- The `START` → `END` block appears directly after `PASTE`
- No extra lines are removed or duplicated
- The rest of the file remains unchanged

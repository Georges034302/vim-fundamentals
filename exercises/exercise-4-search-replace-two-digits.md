# Exercise 4 – Pattern-Based Search and Replace in Vim

## Exercise Objective

The goal of this exercise is to:

- Identify **two-digit numbers** using a search pattern
- Replace **all two-digit numbers** in the file with the character `#`
- Preserve all other text unchanged

This exercise reinforces:

- Searching using **patterns**, not literal words
- Global substitution using Vim’s substitute command
- Careful validation before saving changes

All commands must be executed in **Normal mode**.

---

## File Used

`exercises/demo.txt`

The file contains multiple sections, including text with **two-digit numbers** such as:

```text
User count: 12
Error threshold: 45
Retry attempts: 99
Timeout value: 30
Batch ID: 27
Process code: 84
```

---

## Task (Student Instructions)

1. Search for **any two-digit number** in the file.
2. Replace **all two-digit numbers** with `#`.
3. Do **not** change:
   - Single-digit numbers
   - Words or surrounding text
4. Save the file and exit Vim.

---

## Hints

- You are replacing a **pattern**, not a specific number.
- A two-digit number consists of **exactly two digits**.
- The substitution should apply to the **entire file**.

---

## Step-by-Step Solution

### 1. Open the file

```bash
vim exercises/demo.txt
```

Vim opens in **Normal mode**.

---

### 2. (Optional) Verify the pattern using search

Search for any two-digit number:

```vim
/[0-9][0-9]
```

Use:

```vim
n
```

to move between matches.

---

### 3. Replace all two-digit numbers

```vim
:%s/[0-9][0-9]/#/g
```

### Explanation

- `:` → enter command-line mode
- `%` → apply to the entire file
- `s` → substitute
- `[0-9][0-9]` → any two-digit number
- `#` → replacement character
- `g` → replace all matches on each line

---

### 4. Save and quit

```vim
:wq
```

---

## Expected Result

After completing the exercise, all two-digit numbers are replaced:

```text
User count: #
Error threshold: #
Retry attempts: #
Timeout value: #
Batch ID: #
Process code: #
```

All other content in the file remains unchanged.

---

## Key Concepts Reinforced

- Regular expressions in Vim searches
- Difference between **search** and **substitute**
- Safe global edits using pattern validation
- Real-world use cases such as data masking and log sanitisation

---

## Common Mistakes

- Replacing only the first match (missing the `g` flag)
- Forgetting `%` and replacing on a single line only
- Using an incorrect pattern that matches more than two digits

---

## Completion Criteria

The exercise is complete when:

- Every two-digit number is replaced with `#`
- No other text is altered
- The file is saved successfully

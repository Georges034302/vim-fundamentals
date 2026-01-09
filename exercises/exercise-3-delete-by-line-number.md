# Exercise 3 – Solution (Delete Using Line Number)

**File:** `demo.txt`  
**Mode:** Normal mode only  

---

## Step 1 — Open the file

```bash
vim demo.txt
```

---

## Step 2 — Show line numbers

```vim
:set number
```

---

## Step 3 — Search for the target line

```vim
/Some unrelated text line 2
```

---

## Step 4 — Note the line number shown

Use the line number displayed on the left.

---

## Step 5 — Go to that line number

```vim
:N
```

(Replace `N` with the number you see)

---

## Step 6 — Delete the line

```vim
dd
```

---

## Step 7 — Hide line numbers

```vim
:set nonumber
```

---

## Step 8 — Save and quit

```vim
:wq
```

---

## Completion Check

- Correct line identified by number
- Only that line deleted
- File saved successfully

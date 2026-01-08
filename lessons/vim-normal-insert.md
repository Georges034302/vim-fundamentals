# Vim Fundamentals – Normal & Insert Mode

## Overview
This lesson introduces Vim using Normal and Insert modes only.

## What is Vim?
Vim is a modal text editor.
- Normal mode: commands
- Insert mode: text

## Mode Switching
i → insert before cursor  
a → insert after cursor  
I → insert at start of line  
A → insert at end of line  
Esc → return to Normal mode

## Moving the Cursor
0 → start of line  
$ → end of line  
w → next word  
b → previous word  
gg → top of file  
G → bottom of file  
:n → go to line n

## Inserting Text
i → insert before cursor  
a → insert after cursor  
A → insert at end of line  

## Cutting Text
d → delete (cut)
dw → cut word  
dd → cut line  
d$ → cut to end of line  

## Copying Text
y → yank (copy)
yw → copy word  
yy → copy line  
y$ → copy to end of line  

## Pasting
p → paste after cursor  
P → paste before cursor  

## Searching
/text → search  
n → next match  
N → previous match  

## Search & Replace
:%s/old/new/g

## Marking
m → mark  
' → jump to mark  

## Other Commands
:set number  
:set nonumber  
J → join lines  
u → undo  
Ctrl+r → redo

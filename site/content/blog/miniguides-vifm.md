---
title: "Miniguides - Vifm"
date: 2020-12-01T12:49:52+02:00
draft: false
tags: [
    "vifm",
    "tabs",
    "panes",
    "directories",
    "files",
    "marks",
    "tags"
]
---

"How do I work with ... in Vifm?" questions should have an answer in here.
<!--more-->

## Commands

```mason
# Run command.
:![command]

# Run command and wait for keypress.
:!![command]

# Open external editor to prompt for command-line command.
q:
```

## Tabs

```mason
# Create new tab.
:tabnew

# Close current tab.
:tabclose
# or
:q
# but 'q' closes the last tab as well.


# Switch tabs.
:tabnext
# or
gt

:tabprevious
# or
gT

# 2nd tab
2gt
```

## Panes

```mason
# Split window horizontally.
Ctrl-W s

# Split window vertically.
Ctrl-W v

# Make size of two views equal.
Ctrl-W =

# Maximize current view by default.
Ctrl-W | 
# or
Ctrl-W _ 

# Leave only one pane.
Ctrl-W o

# Scroll down half page.
Ctrl-D

# Scroll up half page.
Ctrl-U

# Clear and redraw the screen.
Ctrl-L
```

## Directories and Files

### Undo, Redo

```mason
# Undo last change.
u

# Redo last change.
Ctrl-R
```

### Select

```mason
# Select in normal mode.
t

# Enter visual select mode, clear current selection.
v
#or
V

# Save selection and go back to normal mode not moving cursor.
Enter

# Enter amending visual mode. Preserves current selections.
av
```

### Operations 

#### Basic

```mason
# Copy.
yy
# or
Y

# Paste.
p

# Move.
P

# Delete to Vifm trash.
dd

# Delete permanently.
DD

# Rename.
cw

# Rename w/o extension.
cW
```

#### Basic++

```mason
# Select directories or files in pwd with `t`, `v`, `av`.
# Store them in a register: e.g. `a`.
# Make another selection in pwd or in another directory.
# Store them in the same register: e.g. `A`.
# Paste or Move the collected files.

```

#### Other

```mason
# Change attributes.
cp

# Clone.
C
```

### Meta

#### Info

```mason
Ctrl-G
```

#### Size

```mason
# Select directory or file
# or
# select top two dots, for all objects in directory,
# and calculate size. 
gA

# Select directory or file
# or
# select top two dots, for all objects in directory,
# and calculate size using using cached sizes
ga
```

#### Marks and Chars

```mason
# Go to a directory or file of interest.
# If directory, select the top line, the two dots at the top.
# Press 'm' and then a char.
# Example: mark '~/Downloads' for 'd'.
md

# To quickly navigate to a mark,
# press apostrophe and then a char.
# Example: jump to previsouly marked '~/Downloads'.
'd

# Example: display menu of all marks.
:marks

# Example: display menu of filtered marks.
:marks d
```

#### Marks and Tags

```mason
# Mark current dir or file with tags using the bmark command.
# Example: mark '~/go' with 'go' and 'golang' tags. 
:bmark go golang

# Mark and tag from everywhere using the 'bmark!' command.
# Example: mark '~/go' with 'go' and 'golang' tags.
:bmark! ~/go go golang

# Example: display menu of all bmarks.
:bmarks

# Example: display menu of filtered bmarks.
:bmarks golang
```

### Search

#### Regular expressions

```mason
# Forward search.
/[regexp]

# Open external editor to prompt for forward search pattern.
q/


# Backward search.
?[regexp]

# Open external editor to prompt for backward search pattern.
q?


# Press 'n' for the next match, 'N' for the previous match.
```

#### First char

```mason
# Forward search.
f[char]

# Backward search.
F[char]

# Press ';' for the next match, ',' for the previous match.
```

### Preview

```mason
# Exit with 'w'.
w

# Scroll with 'Ctrl-D'/'Ctrl-U'. Exit with 'q'.
e
```

### Filter

#### dot directories and files

```mason
# Toggle visibility.
za
```

#### Other
```mason
# Save and reset all filters.
zR

# Open external editor to prompt for filter pattern.
q=
```

## Directories

### History

```mason
# Go to last visited directory.
:cd -

# Go backwards through directory history of current view.
:histprev
# or default keybinding
Ctrl-O

# Go forward through directory history of current view.
:histnext

# Display a menu with list of visited directories.
:history
```

## Files

## Reading list

[Vifm - Manual in Vimdoc format](https://vifm.info/vimdoc.shtml)


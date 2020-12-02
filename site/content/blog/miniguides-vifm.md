---
title: "Miniguides - Vifm"
date: 2020-12-01T12:49:52+02:00
draft: false
tags: [
    "vifm",
    "tabs",
    "panes",
    "directories",
    "marks",
    "tags"
]
---

"How do I work with ... in Vifm?" questions should have an answer in here.
<!--more-->

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
Ctrl-W _ 
```

## Directories

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

## Delete permanently.
DD

# Rename.
cw

# Rename w/o extension
cW
```

### Meta

#### Size
```mason
# Select directory
# or
# select top two dots, for all objects in directory,
# and calculate size. 
gA

# Select directory
# or
# select top two dots, for all objects in directory,
# and calculate size using using cached sizes
ga
```

#### History
```mason
# Go backwards through directory history of current view.
:histprev
# or default keybinding
Ctrl-O

# Go forward through directory history of current view.
:histnext

# Display a menu with list of visited directories.
:history
```

#### Marks and Chars
```mason
# Go to a folder of interest
# Select the top line, the two dots at the top.
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
# Mark the pwd with tags using the bmark command.
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

## Reading list

[Vifm - Manual in Vimdoc format](https://vifm.info/vimdoc.shtml)


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
    "tags",
    "path",
    "vim",
    "clipboard",
    "multiselect"
]
---

"How do I work with ... in Vifm?" questions should have an answer below.
<!--more-->

## Recipes

### MultiSelect

```mason
# Select randomly in normal mode.
t

# Enter amending visual mode, preserving the current selections.
# Add continuous selection.
av

# Go back to normal mode (not moving cursor) and save selection.
Enter
```
### Collect directories and files from different paths to a register

```mason
# Select directories or files in pwd.
# Store selected items in a register: e.g. `a`.
"ayy

# Make another selection in pwd or in another directory.
# Append them using the appropriate uppercase register: e.g. `A`.
"A

# Paste or Move the collected directories and files.
p
# or
P
# or 
"ap
# or
"Ap
```

### Copy file name and path to clipboard

#### Using macros

```mason
# `%c` is the file name macro.
# `:p` is the full path file name modifier.
# `%m` redirects command output to a menu.
:!echo %c:p %m

# Insert menu option to command line.
c

# Delete starting `!` prefix.
Home, Del

# Edit command-line content in external editor: vim.
Ctrl-G

# Vim commands: use of the `+` special register.
# Copy the top line to system clipboard.
"+yy
```

#### Using keys

```mason
# Enter command mode.
:

# Insert value: path to the current directory of the active pane.
Ctrl-X d

# Add path delimiter.
/

# Insert value: name of the current file of the active pane.
Ctrl-X c

# Edit command-line content in external editor: vim.
Ctrl-G

# Vim commands: use of the `+` special register.
# Copy the top line to system clipboard.
"+yy
```

## Commands

```mason
# Run command.
:![command]

# Run command and wait for keypress.
:!![command]

# Open external editor to prompt for command-line command.
q:

# You can give multiple commands in one line.
# '|' can be used to separate commands.
:!!zip -sf %c | less

# Macro:
# show command output in a menu;
# exit with 'Esc'.
:!ls %m

# Macro:
# show command output in the status bar.
:!ls %S

# Macro:
# redirect command output to quick view, which is activated if disabled;
# exit with 'w'.
:!ls %q

# Macro:
# ignore command output.
:!ls %i
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

## Reading list

[Vifm - Manual in Vimdoc format](https://vifm.info/vimdoc.shtml)


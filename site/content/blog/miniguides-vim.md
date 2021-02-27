---
title: "Miniguides - Vim"
date: 2021-02-26T21:02:53+02:00
draft: false
tags: [
    "vim",
    "horizontal",
    "scroll",
    "nowrap"
]
---

"How do I work with ... in Vim?" questions should have an answer below.
<!--more-->

## Recipes

### Scroll horizontally

```mason
# Add nowrap settings to $MYVIMRC
set formatoptions-=t
set textwidth=0
set wrapmargin=0

# Scroll half screenwidth to the right
zL

# Scroll half screenwidth to the left
zH
```

## Reading list

[Vim help files](https://vimhelp.org/)


---
title: "Heap Miscellanea"
date: 2021-02-28T11:29:08+02:00
draft: false
tags: [
    "hugo",
    "static",
    "site",
    "debian",
    "package",
    "list"
]
---

Random knowledge base access center.
<!--more-->

## Debian

### List installed packages

```mason
dpkg-query -l
```

## Hugo

### Create a new blog entry

```mason
# Navigate to the 'site' directory
hugo new blog/heap-miscellanea.md
```

### Create a new release
```mason
# Navigate to the 'site' directory
# Delete the 'public' subdirectory
hugo

# Navigate up directory
cd ..

# Commit and push changes
# If github and netlify have been set up so,
# the new release should be published automatically
```

## Reading list

[Debian Wiki - List installed packages](https://wiki.debian.org/AptCLI#List_installed_packages)

[Hugo - Quick Start](https://gohugo.io/getting-started/quick-start/)


---
title: "Permissions for files and directories"
date: 2020-11-25T22:14:35+02:00
draft: false
tags: [
    "debian",
    "permissions",
    "font",
    "Anonymous",
    "vifm",
]
---

Troubleshoot checklist item #99: missing permissions on files or directories.
<!--more-->

## A suficiently trivial task

Add a custom font for the current user in Debian: [Anonymous Font](https://www.fontspace.com/anonymous-font-f3245). Permissions for the font file are key, "otherwise it may not be usable".

## Prerequisites

Downloaded zip archive for the Anonymous Font is found in the `Downloads` directory in the user home directory.

## Use the command prompt

```sh
# List the files in the downloaded archive.
unzip -l ~/Downloads/anonymous-font.zip

# Unzip the ttf file to ~/.fonts/.
unzip ~/Downloads/anonymous-font.zip *.ttf -d ~/.fonts/ 

# Check if the font is recognized. 
fc-list | grep "Anon"

# Nothing listed? Check the file permissions.
ls -l ~/.fonts/ | grep "Anon"

# Change permissions for each category.
find ~/.fonts/ -name "Anon*" | xargs chmod u=rw
find ~/.fonts/ -name "Anon*" | xargs chmod g=r
find ~/.fonts/ -name "Anon*" | xargs chmod o=r

# Alternatively, by combining categories with similar permissions.
find ~/.fonts/ -name "Anon*" | xargs chmod u=rw
find ~/.fonts/ -name "Anon*" | xargs chmod go=r

# Alternatively, in one go for all categories, with the numeric method: r=4, w=2, x= 1.
find ~/.fonts/ -name "Anon*" | xargs chmod 644

# Rebuild cached list of fonts.
fc-cache -fv

# Check again if the font is recognized.
fc-list | grep "Anon"
``` 

## Use vifm

Navigate to the downloaded zip file. 

Enter command mode and issue unzip commands for archive file list and for extracting the `ttf` files only, if any.

```sh
:!!unzip -l %f
:!unzip %f *.ttf  
```

Navigate to the extracted files and check the file permissions displayed in the `vifm` status bar.

Select the `ttf` files: `t` or enter the visual mode `v`.

`cp` for file properties dialog.

Select the `rwx` attributes for each category: `rw` for `u`ser, `r` for `g`roup, `r` for `o`thers.

Select the `ttf` files: `t` or enter the visual mode `v`.

`yy`ank them.

Navigate to `~/.fonts`, `P`aste with moving the files also (`p` for copy).

Rebuilding cached list of fonts is usually not neccessary when following these steps.

Check if the font is recognized.

```sh
:!!fc-list | grep "Anon"
```

## Reading list

[Fonts - Debian Wiki](https://wiki.debian.org/Fonts)

[File permissions and attributes - ArchLinux Wiki](https://wiki.archlinux.org/index.php/File_permissions_and_attributes)


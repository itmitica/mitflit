---
title: "Golang Paths of Mitflit"
date: 2020-11-26T17:45:42+02:00
draft: false
tags: [
    "golang",
    "shellvars",
    "envvars",
    "paths",
    "GOBIN",
    "GOCACHE",
    "GOENV",
    "GOPATH",
    "GOROOT",
    "modules",
    "debian",
    "windows",
]
---

Where I change the default paths in golang to a centralized location on disk.
<!--more-->

## Golang paths of default

Use an installer. Take note of the installation path, it becomes `GOROOT`. Installer will also add `GOROOT/bin` to the path. 

Don't use an installer. Extract to a directory of my choice. Set `GOROOT` manually. Add `GOROOT/bin` to path manually.

Run `go env`. Observe default path settings.

The default `GOPATH` is `go` on the user home directory. I am not to use the default `GOPATH` for `GOROOT`. I should add `GOPATH/bin` to path manually if `GOBIN` is not set.

The default `GOBIN` is `GOPATH/bin`. If `GOBIN` is set, then I should add that to path manually.

The default `GOCAHE` is in a `build` directory somewhere in the user home directory.

The default `GOENV` file `env` is stored somewhere else in the user home directory.

## Golang paths of mitflit

Paths in symmetry with the environmental variables: `GOROOT` is `go/root`, `GOPATH` is `go/path`, `GOBIN` is `go/bin`. `GOCACHE` is `go/cache`, `GOENV` is `go/env`. Bonus points: modules in `go/modules`, `env` in `go/env`.

```
├─ go
│  ├─ bin      (GOBIN, where install command deploys binaries)
│  ├─ build    (GOCACHE, where cached builds await reuse)
│  ├─ modules
│  ├─ path     (GOPATH, first workspace, where downloaded packages are)
│  └─ root     (GOROOT, golang installation goes here)
│     env      (GOENV, the golang config file)
```

### Prerequisites

Downloaded golang binary release archive, `tar.gz` for Debian or `zip` for Windows, is found in the `Downloads` directory in the user home directory.

Previous golang installation or usage has been purged: target `go` directory has no tree structure pertaining to a default `GOROOT` or `GOPATH`.

### Debian
```sh
# Check if golang shellvars or envvars are already set.
set | grep GO
printenv | grep GO

# Create golang folders.
mkdir ~/go
mkdir ~/go/bin
mkdir ~/go/cache
mkdir ~/go/modules
mkdir ~/go/path

# Delete the old golang version.
rmdir ~/go/root

# Unzip the new version.
tar -C ~/go -xzf ~/Downloads/go*.tar.gz

# Rename the extracted top folder.
mv -T ~/go/go ~/go/root

# Temporarly set the shellvars, for the current process.
GOENV=~/go/env
PATH=$PATH:$GOROOT/bin:$GOBIN

# Temporarly set the envvars, for the current process.
export GOENV
export PATH

# Set the envvars for future sessions.
echo "export GOENV=$GOENV" >>~/.profile
echo "export PATH=$PATH" >>~/.profile

# Set the rest of the envvars in the env file.
go env -w GOBIN=~/go/bin
go env -w GOCACHE=~/go/cache
go env -w GOPATH=~/go/path
go env -w GOROOT=~/go/root
```

### Windows

As far as I know, it's not possible to append only to the User Paths in a simple manner, using the command line. The next best thing is to simply use the `Control Panel/System` GUI to add `%GOROOT%\bin` and `%GOBIN%` to User Paths.

```batchfile
REM Create golang folders.
mkdir e:\projects\go
mkdir e:\projects\go\bin
mkdir e:\projects\go\cache
mkdir e:\projects\go\modules
mkdir e:\projects\go\path

REM Delete the old golang version.
rmdir e:\projects\go\root

REM Unzip the new version.
"%ProgramFiles%\7-zip\7z.exe" x -oe:\projects\go "%USERPROFILE%\Downloads\go*.zip"

REM Rename the extracted top folder.
ren e:\projects\go\go root

REM Temporarly set the envvars for the current session.
set GOENV=e:\projects\go\env

REM Set the envvars for future sessions.
setx GOENV $GOENV

REM Set the rest of the envvars in the env file.
%GOROOT%\bin\go env -w GOBIN=e:\projects\go\bin
%GOROOT%\bin\go env -w GOCACHE=e:\projects\go\cache
%GOROOT%\bin\go env -w GOPATH=e:\projects\go\path
%GOROOT%\bin\go env -w GOROOT=e:\projects\go\root
```

## Reading list

[How To Read and Set Environmental and Shell Variable on Linux | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)


---
title: "Golang Paths of Mitflit"
date: 2020-11-26T17:45:42+02:00
draft: true
tags: [
    "golang",
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

Paths in symmetry with the environmental variables: `GOROOT` is `go/root`, `GOPATH` is `go/path`, `GOBIN` is `go/bin`. `GOCACHE` is `go/cache`, `GOENV` is `go/env`. Bonus points: modules in `go/modules`, `env` in `go/env`.
<!--more-->

## Golang paths of default

Use an installer. Take note of the installation path, it becomes `GOROOT`. Installer will also add `GOROOT/bin` to the path. 

Don't use an installer. Extract to a directory of my choice. Set `GOROOT` manually. Add `GOROOT/bin` to path manually.

Run `go env`. Observe default path settings.

The default `GOPATH` is `go` on the user home directory. I am not to use the default `GOPATH` for `GOROOT`. I should add `GOPATH/bin` to path manually if `GOBIN` is not set.

The default `GOBIN` is `GOPATH/bin`. If `GOBIN` is set, then I should add that to path manually.

The default `GOCAHE` is in a `build` directory somewhere.

The default `GOENV` file `env` is stored somewhere else.


## Golang paths of mitflit

Set the envvars for paths manually. Use the same tree structure on all platforms.

```
├─ go
│  ├─ bin      (GOBIN, where install command deploys binaries)
│  ├─ build    (GOCACHE, where cached builds await reuse)
│  ├─ modules
│  ├─ path     (GOPATH, first workspace, where downloaded packages are)
│  └─ root     (GOROOT, golang installation goes here)
│     env      (GOENV, the golang config file)
```

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

# Temporarly set the shellvars for paths, for the current process.
GOENV=~/go/env
GOBIN=~/go/bin
GOCACHE=~/go/cache
GOPATH=~/go/path
GOROOT=~/go/root
PATH=$PATH:$GOROOT/bin:$GOBIN

# Temporarly set the envvars for paths, for the current process.
export GOENV
export GOBIN
export GOCACHE
export GOPATH
export GOROOT
export PATH

# Set the envvars for paths for future sessions.
echo "export GOENV="$GOENV >>~/.profile
echo "export GOBIN="$GOBIN >>~/.profile
echo "export GOCACHE="$GOCACHE >>~/.profile
echo "export GOPATH="$GOPATH >>~/.profile
echo "export GOROOT="$GOROOT >>~/.profile
echo "export PATH="$PATH >>~/.profile

# Set the envvars for paths in the env file as well.
go env -w GOENV=$GOENV
go env -w GOBIN=$GOBIN
go env -w GOCACHE=$GOCACHE
go env -w GOPATH=$GOPATH
go env -w GOROOT=$GOROOT

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

REM Temporarly set the envvars for paths, for the current session.
set GOENV=e:\projects\go\env
set GOBIN=e:\projects\go\bin
set GOCACHE=e:\projects\go\cache
set GOPATH=e:\projects\go\path
set GOROOT=e:\projects\go\root
set PATH="%PATH%;%GOROOT%\bin"

REM Set the envvars for paths for future sessions.
setx GOENV e:\projects\go\env
setx GOBIN e:\projects\go\bin
setx GOCACHE e:\projects\go\cache
setx GOPATH e:\projects\go\path
setx GOROOT e:\projects\go\root

REM Set the envvars for paths in the env file as well.
%GOROOT%\bin\go env -w GOBIN=e:\projects\go\bin
%GOROOT%\bin\go env -w GOCACHE=e:\projects\go\cache
%GOROOT%\bin\go env -w GOPATH=e:\projects\go\path
%GOROOT%\bin\go env -w GOROOT=e:\projects\go\root
REM setx PATH "%PATH%;%GOROOT%\bin;%GOBIN%"
REM The above command has the side effect
REM of adding the System Paths to User Paths.
REM Best way is to use the GUI in Control Panel/System
REM to add GOROOT/bin and GOBIN to User Paths.
```
## Reading list

[How To Read and Set Environmental and Shell Variable on Linux | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)


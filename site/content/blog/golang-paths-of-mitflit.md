---
title: "Golang Paths of Mitflit"
date: 2020-11-26T17:45:42+02:00
draft: true
tags: [
    "debian",
    "windows",
    "golang",
    "paths",
    "GOBIN",
    "GOPATH",
    "GOROOT",
    "modules",
]
---

`GOROOT` in `go/root`, `GOPATH` in `go/path`, `GOBIN` in `go/bin`. Modules in `go/modules`.
<!--more-->

## Golang paths of default

Use an installer. Take note of the installation path, it becomes `GOROOT`. Installer will also add `GOROOT/bin` to the path. 

Don't use an installer. Extract to a directory of my choice. Set `GOROOT` manually. Add `GOROOT/bin` to path manually.

The default `GOPATH` is `go` on the user home directory. I am not to use the default `GOPATH` for `GOROOT`.

The default `GOBIN` is `GOPATH/bin`.

## Golang paths of mitflit

I set my paths manually, the same tree structure on all platforms.

```
├─ go
│  ├─ bin      (GOBIN,  where install command deploys binaries)
│  ├─ modules
│  ├─ path     (GOPATH, first workspace, where downloaded packages are)
│  └─ root     (GOROOT, golang installation goes here)
```

### Unix-like
```sh
# Set the paths for future sessions.
go env -w GOBIN =$HOME/go/bin
go env -w GOPATH=$HOME/go/path
go env -w GOROOT=$HOME/go/root
```

### Windows
```batchfile
REM Create golang folders.
mkdir c:\go
mkdir c:\go\bin
mkdir c:\go\modules
mkdir c:\go\path

REM Delete the old golang version.
rmdir c:\go\root

REM Unzip the new version.
"%ProgramFiles%\7-zip\7z.exe" x -oc:\go "%USERPROFILE%\Downloads\go*.zip"

REM Rename the extracted top folder.
ren c:\go\go root

REM Set the paths for the current session.
set GOBIN =c:\go\bin
set GOPATH=c:\go\path
set GOROOT=c:\go\root
set PATH="%PATH%;%GOROOT%\bin"

REM Set the paths for future sessions.
go env -w GOBIN =c:\go\bin
go env -w GOPATH=c:\go\path
go env -w GOROOT=c:\go\root
REM setx PATH "%PATH%;%GOROOT%\bin;%GOBIN%"
```


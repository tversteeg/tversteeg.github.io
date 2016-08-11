---
title:        "Detect OS with autoconf"
# jekyll-seo-tag
description:  ""
author:       "tversteeg"
---

In this (first) blog post based on my [answer](http://stackoverflow.com/a/38899152/1350184) for a Stack Overflow question I'll show you how to detect the _target OS_ in the `configure.ac` or `configure.in` autotools-files. 

It's important to notice that with target I refer to the target OS when cross-compiling, for example: you are cross-compiling a Windows `bin.exe` executable file from GNU/Linux, the target would be Windows.

- - - 

Add the following code to your `configure.ac` somewhere between `AC_INIT` and `AC_OUTPUT`:

``` Make
...

# AC_CANONICAL_HOST is needed to access the 'host_os' variable    
AC_CANONICAL_HOST

build_linux=no
build_windows=no
build_mac=no

# Detect the target system
case "${host_os}" in
    linux*)
        build_linux=yes
        ;;
    cygwin*|mingw*)
        build_windows=yes
        ;;
    darwin*)
        build_mac=yes
        ;;
    *)
        AC_MSG_ERROR(["OS $host_os is not supported"])
        ;;
esac

# Pass the conditionals to automake
AM_CONDITIONAL([BUILD_LINUX], [test "$build_linux" = "yes"])
AM_CONDITIONAL([BUILD_WIN32], [test "$build_windows" = "yes"])
AM_CONDITIONAL([BUILD_OSX], [test "$build_mac" = "yes"])

...
```

This sets the `BUILD_*` conditionals which we can use in our example `Makefile.am`:

``` Make
...

APP_SOURCES = src/main.c

if BUILD_LINUX
APP_SOURCES += src/linux_dep.c
endif
if BUILD_WIN32
APP_SOURCES += src/win32_dep.c
endif
if BUILD_OSX
APP_SOURCES += src/osx_dep.c
endif

...
```

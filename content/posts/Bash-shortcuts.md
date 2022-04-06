---
title: "Bash, Productivity Shortcuts"
description: A collection of keyboard shortcuts that improve productivity in Bash.
date: 2022-04-06T17:13:00+01:00
draft: false
toc: true
featuredImage: ''
tags: [Bash, WSL]
categories: [Linux]
---

Working in a command line environment, like a Bash session, can be far more productive that using a graphical user interface.  Here's a collection of keyboard shortcuts.

<!--more-->

## Moving Around The Command Line

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
|<kbd>Ctrl</kbd> + <kbd>a</kbd> | position cursor at the start of the line |
|<kbd>Ctrl</kbd> + <kbd>e</kbd> | position cursor at the end of the line |
|<kbd>Ctrl</kbd> + <kbd>xx</kbd> | alternates the cursor position between start of line and current position |
|<kbd>Ctrl</kbd> + <kbd>w</kbd> | cut backward a word |
|<kbd>Ctrl</kbd> + <kbd>u</kbd> | cut backward from the cursor to start of line |
|<kbd>Ctrl</kbd> + <kbd>k</kbd> | cut forward from the cursor to end of line |
|<kbd>Ctrl</kbd> + <kbd>y</kbd> | paste the contents of the *cut buffer* |
|<kbd>Esc</kbd> + <kbd>.</kbd> | paste the the last typed argument |
|<kbd>Ctrl</kbd> + <kbd>_</kbd> | undo |
|<kbd>Ctrl</kbd> + <kbd>l</kbd> | clear the screen |
|<kbd>Ctrl</kbd> + <kbd>d</kbd> | disconnect (exit) the current session |

## Using Command Line History

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
| ```history``` | view command history, with line numbers |
| ```!n``` | retrieve the command at line *n* |
| ```sudo !!``` | re-execute the last typed command, but with *sudo* |
|<kbd>Ctrl</kbd> + <kbd>r</kbd> | *search history* mode, type a few characters, repeat press <kbd>Ctrl</kbd> + <kbd>r</kbd> for next match |
|<kbd>Ctrl</kbd> + <kbd>g</kbd> | escape *search history* mode |

## Navigating Directories

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
| ```cd``` | go to *home* folder (same as ```cd ~```) |
| ```cd -``` | go to previous working folder |
| ```pushd /etc``` | push the current directory to the *directory stack*, then `cd` to `/etc` |
| ```pushd /var``` | push the current directory to the *directory stack*, then `cd` to `/var` |
| ```popd``` | remove the top directory from the *directory stack*, then `cd` to it |
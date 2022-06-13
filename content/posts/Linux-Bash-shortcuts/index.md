---
title: "Bash: Productivity Shortcuts"
description: A collection of keyboard shortcuts that improve productivity in Bash.
date: 2022-04-08T20:13:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Bash, WSL]
categories: [Linux]
---

Working in a command line environment, like a Bash session, can be far more productive that using a graphical user interface.  Here's a collection of shortcuts.

<!--more-->

## Moving Around The Command Line

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
|<kbd>Ctrl</kbd> + <kbd>a</kbd> | position the cursor at the start of the line |
|<kbd>Ctrl</kbd> + <kbd>e</kbd> | position the cursor at the end of the line |
|<kbd>Ctrl</kbd> + <kbd>xx</kbd> | alternate the cursor position between start of line and current position |
|<kbd>Alt</kbd> + <kbd>b</kbd> | move the cursor backwards a word |
|<kbd>Alt</kbd> + <kbd>f</kbd> | move the cursor forewards a word |
|<kbd>Ctrl</kbd> + <kbd>w</kbd> | cut backwards a word |
|<kbd>Ctrl</kbd> + <kbd>u</kbd> | cut backwards from the cursor to start of line |
|<kbd>Ctrl</kbd> + <kbd>k</kbd> | cut forwards from the cursor to end of line |
|<kbd>Ctrl</kbd> + <kbd>y</kbd> | paste the contents of the *paste buffer* |
|<kbd>Esc</kbd> + <kbd>.</kbd> | paste the the last typed argument |
|<kbd>Ctrl</kbd> + <kbd>_</kbd> | undo |
|<kbd>Ctrl</kbd> + <kbd>l</kbd> | clear the screen |
|<kbd>Ctrl</kbd> + <kbd>c</kbd> | cancel the current running command |
|<kbd>Ctrl</kbd> + <kbd>d</kbd> | disconnect (exit) the current session |

## Using Command Line History

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
| ```history``` | view command history, with line numbers |
| ```!n``` | retrieve the command at line number *n* |
| ```!-n``` | retrieve the *nth* last command |
| ```!string``` | retrieve the command that starts with *string* |
| ```sudo !!``` | re-execute the last command, but with *sudo* |
| ```^string^newstring^``` | re-execute the last command, replacing *string* with *newstring* |
|<kbd>Ctrl</kbd> + <kbd>r</kbd> | begin *search history mode*, type a few characters, <br /> repeat press <kbd>Ctrl</kbd> + <kbd>r</kbd> for next match |
|<kbd>Ctrl</kbd> + <kbd>g</kbd> | escape *search history mode* |

### Managing Command Line History

Prevent a command from being written to history... precede the command with a space, like this:

```Bash
 cat ~/.bashrc
```

Reliably delete all history, clear the *history buffer* and prevent history from being re-written on exit:

```Bash
cat /dev/null > ~/.bash_history && history -c && exit
```

## Navigating Directories

| Shortcut  | Function                                      |
|-----------|-----------------------------------------------|
| ```cd``` | go to *home* directory (same as ```cd ~```) |
| ```cd -``` | go to previous working directory |
| ```pushd /foo``` <br /> <br /> ```pushd /bar``` | push the current directory to the *directory stack*, <br /> then `cd` to the `/foo` directory <br /> push the current directory to the *directory stack*, <br /> then `cd` to the `/bar` directory |
| ```popd``` | remove the top directory from the *directory stack*, then `cd` to it |

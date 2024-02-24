---
title: "Install Manim On Windows 11 & Windows 10"
description: How to install the animation generation tool, Manim Community Edition, on Windows.
date: 2022-03-02T13:20:01+00:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Python, LaTeX, KaTeX]
categories: [Windows, Documentation]
---

Manim is a Python based tool that creates animations of math and technical concepts.

<!--more-->

> This blog post covers how to install Manim Community Edition on Windows 10 & 11. For a more detailed description of the installation method, including for other OSs, Docker and web, visit the official [Manim Community Edition installation pages](https://docs.manim.community/en/stable/installation.html).

## Getting Your System Ready For Manim Community Edition

### Python

Manim requires Python.  If your Windows device has [winget](https://docs.microsoft.com/en-us/windows/package-manager/winget/), install Python with:

```Batchfile
winget install Python.Python.3
```

If you don't have `winget`, then [download the Python installer](https://www.python.org/downloads/).

### MikTex

This is optional, but recommended. Installing MikTex will enable Manim to draw equations (such as $y=x^2$) in your animations.

```Batchfile
winget install ChristianSchenk.MiKTeX
```

If you don't have `winget`, then [download the MikTex installer](https://miktex.org/download).

### Ffmpeg

Manim requires Ffmpeg, to generate animations as video files. At the time of writing, Ffmpeg is not available to install via ```winget```.

1. Download .zip file [ffmpeg-master-latest-win64-gpl.zip](https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip) from the releases page of the [GitHub repository](https://github.com/BtbN/FFmpeg-Builds/releases).
1. Unzip the archive to extract folder `ffmpeg-master-latest-win64-gpl`, move this folder into your `Documents` folder. For example if the Windows user is called *fred* then `Documents` would be located at `C:\Users\fred\Documents`.
1. To enable Manim to find Ffmpeg, add a new entry to `Path`, in the *User* section of *Environment variables*, do that by...
    1. Press the <kbd>Windows</kbd> key and start typing "env", select the top search result "Edit the system environment variables".
    1. The `System Properties` window will appear, click the button `Environment Variables...`.
    1. A 2nd window will appear, titled `Environment Variables`.  In the top section, titled `User variables for fred`, click the entry labelled `Path`, then the `Edit...` button.
    1. A 3rd window wil be displayed, titled `Edit environment variable`, click on the `New` button.
    1. Enter the full path to the `bin` folder within `ffmpeg-master-latest-win64-gpl`, for example:
        `C:\Users\fred\Documents\ffmpeg-master-latest-win64-gpl\bin`
    1. Click the ```Ok``` button.  Close all 3 windows regarding environment variables.

> To ensure all of the above changes have taken effect, restart the PC.

## Installing Manim

### Python Virtual Environments

> Manim is a Python package, installed by Python's package manager, `pip`. To reduce future problems caused dependency conflicts, Manim can be installed in a Python virtual environment.

1. Create a new folder, to contain your Python (Manim) project, for example `ManimDev`.
1. Within `ManimDev`, open a terminal, create a new Python virtual environment, called ".venv"
    ```text
    python -m venv .venv
    ```
1. Start *.venv*
    ```text
    .venv\scripts\activate
    ```
1. Install Manim
    ```text
    pip install manim
    ```

#### Stopping & Restarting The Python Virtual Environment

To stop the *.venv* virtual environment 

```Batchfile
deactivate
```

Restart *.venv* with...

```Batchfile
.venv\scripts\activate
```
---
title: Installing pydonhive on Windows
summary: How to install the hive (pydongui) on Windows
layout: documentation
type: guide
date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
    - todo
---

# Installation

{% include pydonhive_installation_short_windows.md %}

{% include dependencies_pydonhive.md %}

Tools needed on Windows:

* 7-zip – to unpack `pyosc.tar.gz`, `XBee-2.0.1.tar.gz` and `pyserial.tar.gz`
* A driver for the coordinator board, either the FTDI driver, or another driver (as for the Arduino Uno).


{% include packagecontents_pydonhive.md %}

# Installation step by step

Step by step instructions are below, also always check the `INSTALL.txt` in the package for the latest information.

> These step by step instructions are basically the commands carried out by the installation script.

The instructions below, need to be executed in the terminal. For each code snippet you see there, you have to copy them literally into the terminal, except when otherwise noted and except for the dollar sign, which indicates the command prompt.

On Windows this is called the “command prompt”, and can be opened from the Windows menu by typing “cmd.exe” in the dialog box that shows up when choosing “Run”. See also specific Windows instructions below.

## [step 0] : install 7-zip


## [step 1] : unpack everything

Unpack the zip-file that you downloaded (`ssdn-python-master`) by doubleclicking on it.

Then:

* Right-click on `pyosc.tar.gz`, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting `pyosc.tar` file. Now you have a folder `pyosc`.

* Right-click on `XBee2.0.1.tar.gz`, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting `XBee2.0.1.tar` file. Now you have a folder `XBee2.0.1`

* Right-click on `pyserial.tar.gz`, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting `pyserial.tar` file. Now you have a folder `pyserial`

## [step 2] : open cmd.exe and navigate

Open cmd.exe from the run menu of Windows.

Unpack the zip-file, and go to the folder you just created.

    C:> cd C:\Users\myusername\Downloads\ssdn_python\

where `C:\Users\myusername\Downloads\ssdn_python\` is the path in your file system.

If you need to switch to another drive you need to type:

    C:> E:

if you want to go to drive “E:”, and then use `cd` (change directory) to navigate to the actual path.

## [step 2] : check Python version

{% include pydonhive_installation_2.md %}

Alternatively you can provide the full path to python when invoking python, e.g.

    C:> C:\Python2-7\python.exe mypythonscript.py

## [step 3] : Install setuptools

Setuptools is a tool to manage dependencies for Python packages, you can get it at [setuptools at pypi.python.org](http://pypi.python.org/pypi/setuptools) and find install instructions there too.

* Navigate to the extracted package
* Type:
```
C:> python ez_setup.py
```

## [step 4] : Install the dependencies:

* Navigate to pyosc and install:
```
C:> cd pyosc
C:> C:\Python2-7\python.exe setup.py install
C:> cd ..
```

* Navigate to XBee.2.0.1 and install:
```
C:> cd XBee2.0.1
C:> C:\Python2-7\python.exe setup.py install
C:> cd ..
```
* Navigate to pyserial and install:
```
C:> cd pyserial
C:> C:\Python2-7\python.exe setup.py install
```

## [step 5] : Pydon
```
C:> cd pydon
C:> C:\Python2-7\python.exe setup.py install
```

For more information on python setup scripts, see the [python documentation](http://docs.python.org/install/index.html).

# Starting the program

You can now start the program with:

    C:> cd scripts
    C:> C:\Python2-7\python.exe pydongui.py

# TODO

- update pyserial bit


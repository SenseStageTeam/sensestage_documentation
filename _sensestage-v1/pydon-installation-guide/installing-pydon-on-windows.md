---
title: Installing Pydon on Windows
summary: How to install Pydon on Windows

layout: guide
type: guide
parent: Pydon Installation Guide
guidestep: 3

creation-date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
---

# Installation

1. Download the Pydon package for Windows from the [Downloads page](/sensestage-v1/downloads)
2. Download and install the FTDI Virtual Com Port drivers for Windows, also from the [Downloads page](/sensestage-v1/downloads). You'll need these for your computer to recognize your coordinator node.
3. Install the latest python 2.7 for windows. It's best to use the msi installer included in the Windows Pydon package you downloaded in step 1. Just double click the installer and follow the instructions, be sure to include Python in your path when given the option. Otherwise follow the default suggestions for settings.
4. Execute the `install_pydon.bat` file by double-clicking. This will install the necessary Python libraries.
5. Execute the `start_pydon.bat` file by double-clicking to start Pydon. This file needs to stay inside the PydonWindowsPackage folder in order for Pydon to work. However, you can move the whole folder as you like.


## Special Note: Installing Python 2.7 on Windows

There is a msi installer included in the pydon download folder that you can use to install Python 2.7 on your system. Make sure to check the option for adding Python to your system path.

By default this installer will create a folder on your machine in the root of the C harddisk. If you go to your file manager you should see a folder `C:\Python27` there. If not, read the steps below.

The `install_pydon.bat` script installs the Hive software itself. The `start_pydon.bat` script starts the Hive after it is installed.


## What to do if the scripts do not work

In some cases the scripts are not working, and after running the installer you will only briefly see a black window which then dissappears.

You can get the full error message if you start the `start_pydon.bat` file from the terminal `cmd.exe`. You can open `cmd.exe` from the startup menu by choosing `Run` and typing `cmd` - you will then be prompted with the `cmd.exe` choice.

Then navigate to the folder where you stored the package you downloaded.

```
C:> cd C:\Users\myusername\Downloads\PydonWindowsPackage\
```

where `C:\Users\myusername\Downloads\PydonWindowsPackage\` is the path in your file system.

If you need to switch to another drive you need to type:

    C:> E:

if you want to go to drive `E:`, and then use `cd` (change directory) to navigate to the actual path.


## Fixing the scripts

One probable cause is that the location where Python is installed is slightly different.

You can fix this by editing the `.bat` files, by opening them with Notepad. The contents of `install_pydon.bat` are:

```
cd %~dp0

cd ssdn_python-master

echo "installing pyserial"
cd pyserial-sensestage
C:\Python27\python.exe setup.py install
cd ..

echo "installing xbee"
cd XBee-2.0.1
C:\Python27\python.exe setup.py install
cd ..

echo "installing pyosc"
cd pyosc
C:\Python27\python.exe setup.py install
cd ..

echo "installing pydon"
cd pydon
C:\Python27\python.exe setup.py install
cd ..

echo "done installing"

cd ..
```
What you need to change is where you find `C:\Python27\python.exe`, you need to replace it to point to the path where Python is installed on your system. So if in the file manager the path you found is: `C:\Python278` then change `C:\Python27\python.exe` to `C:\Python278\python.exe` everywhere where it appears in the `install_pydon.bat` file. After making the changes, save the file.

The file `start_pydon.bat` looks like this:

```
cd %~dp0
cd ssdn_python-master
cd pydon
cd scripts
C:\Python27\python.exe pydongui.py
```

Here also change `C:\Python27\python.exe` to `C:\Python278\python.exe` everywhere where it appears in the `start_pydon.bat` file. After making the changes, save the file.

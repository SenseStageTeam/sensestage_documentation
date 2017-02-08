---
title: Installing pydonhive on Windows
summary: How to install the hive (pydongui) on Windows
layout: documentation
type: guide
date: 2017-02-06
category: software
subcategory: installation
---

# Installation

- Download the [pydon package for windows](https://sensestage.eu/downloads/PydonWindowsPackage.zip)
- Download and install [Windows usb serial driver](http://arduino.cc/en/Guide/Windows#toc4)
- Install latest python for windows using the msi installer in the pydon package you downloaded (32 bit or 64 bit). Just doubleclick and follow instructions, just follow the default suggestions for settings.
- Execute the ```install_pydon.bat``` file by doubleclicking
- Execute the ```start_pydon.bat``` file by doubleclicking to start pydongui


# Dependencies

Dependencies are:

* python (version 2.6 or higher; but NOT version 3 or higher) – [http://docs.python.org/index.html](), or e.g. [http://www.python.org/download/releases/2.7.6/]()
* pyOSC – [http://gitorious.org/pyosc]() (included in the packaged version)
* python-xbee-api (XBee-2.0.1) – (included in the packaged version)
* pyserial (version 2.6 or higher) – [http://pyserial.sourceforge.net/]() – (included in the packaged version)

Optional dependencies:

* libmapper – check the information at [http://www.idmil.org/software/]() libmapper


Tools needed on Windows:

* 7-zip – to unpack `pyosc.tar.gz`, `XBee-2.0.1.tar.gz` and `pyserial.tar.gz`
* A driver for the coordinator board, either the FTDI driver, or another driver (as for the Arduino Uno).


# What is in the package

In the download package you’ll find two folders and a few files:

* `README.txt` – short introduction
* `INSTALL.txt` – details how to install the package and its dependencies
* `GETTING_STARTED.txt` – gives a quick overview on how to start with the MiniBees you just got and how to interface with them.
* `MINIHIVEOSC_DOCUMENTATION.txt` gives an overview of the OSC interface of MiniHiveOsc, one of the ways to interface with the minibees through the SenseWorld DataNetwork
* `TODO.txt` – todo list for pydon
* `pydon` – this is the actual pydon package, with inside it:
    * A folder `scripts` – the python datanetwork client library, containing:
        * `pydongui.py` – an encapsulating program, providing a GUI-interface for metapydonhive.
        * `pydoncli.py` – an encapsulating program, providing a command line interface for metapydonhive.
    * A folder `pydon` – the python datanetwork client library, containing:
        * `pydon.py` – the python datanetwork client
        * `pydonhive.py` – the python MiniBee management – serial communication component
        * `minibeexml.py` – implementing reading and writing the minibee configurations as an XML file
        * `swpydonhive.py` – gluing pydon.py and pydonhive.py together to a Python “hive” client to the DataNetwork. This is the program you will use to hook up your MiniBees to the DataNetwork.
        * `lmpydonhive.py` – gluing pydonhive.py to libmapper together to a Python “hive” libmapper client. See IDMIL’s website.
        * `minihiveosc.py` – a simple program to communicate to the MiniBee network with a simple OSC interface (sends the data from the minibees to one IP/port via OSC; not using the DataNetwork).
        * `minihivejunxion.py` – a simple program to communicate with the MiniBee network to and from Junxion with a simple OSC interface (not using the DataNetwork).
        * `metapydonhive.py` – an encapsulating program, where you can select one of the possible interfaces to use (datanetwork, osc, junxion, libmapper).
        * `pydonguifront.py` – an encapsulating program, providing a GUI-interface for metapydonhive.
        * `pydonlogger.py` – a helper utility to log the output into both the GUI window of pydongui, and a log file.
    * A folder `configs` – containing some example configuration files.
    * `supercollider` – containing a few test scripts to interface with pydon.
    * `pyosc.tar.gz` – a compressed archive containing pyosc.
    * `XBee-2.0.1.tar.gz` – a compressed archive containing a slightly modified version of the python-xbee library.
    * `pyserial.tar.gz`


# Installation step by step

Step by step instructions are below, also always check the INSTALL.txt in the package for the latest information.

> These step by step instructions are basically the commands carried out by the installation script.

The instructions below, need to be executed in the terminal. For each code snippet you see there, you have to copy them literally into the terminal, except when otherwise noted and except for the dollar sign, which indicates the command prompt.

On Windows this is called the “command prompt”, and can be opened from the Windows menu by typing “cmd.exe” in the dialog box that shows up when choosing “Run”. See also specific Windows instructions below.

## [step 0] : install 7-zip


## [step 1] : unpack everything

Unpack the zip-file that you downloaded (ssdn-python-master) by doubleclicking on it.

Then:

* Right-click on pyosc.tar.gz, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting pyosc.tar file. Now you have a folder pyosc.


* Right-click on XBee2.0.1.tar.gz, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting XBee2.0.1.tar file. Now you have a folder XBee2.0.1

* Right-click on pyserial.tar.gz, in the context menu there should be an entry “7-zip”, select that and choose “extract here”.
* Then do the same again on the resulting pyserial.tar file. Now you have a folder pyserial

## [step 2] : open cmd.exe and navigate

Open cmd.exe from the run menu of Windows.

Unpack the zip-file, and go to the folder you just created.

    C:> cd C:\Users\myusername\Downloads\ssdn_python\

where `C:\Users\myusername\Downloads\ssdn_python\` is the path in your file system.

On Windows paths are using backslashes (\) rather than forward slashes (/). If you need to switch to another drive you need to type:

    C:> E:

if you want to go to drive “E:”, and then use “cd” to navigate to the actual path.

## [step 2] : check Python version

On some operating systems python will already be installed, before you go on, check whether you have the right version:

check which version you have:
    $ python --version
If it is lower than 2.6 you will need to get a version higher than 2.6, but below version 3.

Make sure Python is in your path, alternatively you can provide the full path to python when invoking python, e.g.

    C:> C:\Python2-7\python.exe mypythonscript.py

## [step 3] : Install setuptools

Setuptools is a tool to manage dependencies for Python packages, you can get it at [setuptools at pypi.python.org](http://pypi.python.org/pypi/setuptools) and find install instructions there too.

* Navigate to the extracted package
* Type:
    $ python ez_setup.py

## [step 4] : Install the dependencies:

* Navigate to pyosc and install:
    cd pyosc
    C:\Python2-7\python.exe setup.py install
    cd ..

* Navigate to XBee.2.0.1 and install:
    cd XBee2.0.1
    C:\Python2-7\python.exe setup.py install
    cd ..

* Navigate to pyserial and install:
    cd pyserial
    C:\Python2-7\python.exe setup.py install


## [step 5] : Pydon

    cd pydon
    C:\Python2-7\python.exe setup.py install


For more information on python setup scripts, see the [python documentation](http://docs.python.org/install/index.html).

# Starting the program

You can now start the program with:

    cd scripts
    C:\Python2-7\python.exe pydongui.py


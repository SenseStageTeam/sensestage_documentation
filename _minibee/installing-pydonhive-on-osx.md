---
title: Installing pydonhive on OSX
summary: How to install the hive (pydongui) on OSX
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

* Download the source: [Python client download](https://github.com/sensestage/ssdn_python) (choose the zip option, or use [this direct link](https://github.com/sensestage/ssdn_python/archive/master.zip))
* Unpack the package. In Finder find the file you just downloaded and double-click it to unzip it.
* Run the ./installation.sh script that is in the package.
    * Open up the Terminal application (you can find it in Applications/Utilities/ or do a Spotlight search for "Terminal").
    * Once your terminal is open, type "cd" followed by a space, and drag the folder you just unzipped from your finder into the terminal window. Hit enter.
    * Now type "sudo ./installation.sh" into the terminal and hit enter.
    * The system will ask for your password. Enter your password and hit enter again (you won't see it as you type, this is normal).

    The commands to type should be similar to these:

```
    cd ~/Downloads/ssdn_python-master
    sudo ./installation.sh
    Password: *
```

# Dependencies

Dependencies are:

* python (version 2.6 or higher; but NOT version 3 or higher) – [http://docs.python.org/index.html](), or e.g. [http://www.python.org/download/releases/2.7.6/]()
* pyOSC – [http://gitorious.org/pyosc]() (included in the packaged version)
* python-xbee-api (XBee-2.0.1) – (included in the packaged version)
* pyserial (version 2.6 or higher) – [http://pyserial.sourceforge.net/]() – (included in the packaged version)

Optional dependencies:

* libmapper – check the information at [http://www.idmil.org/software/]() libmapper


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

On OSX you can find the program `Terminal` in the `Applications` folder, in the folder `Utilities`. Or with the Spotlight search.

## [step 1] : unpack the package

Unpack the zip-file, and go to the folder you just created.

    $ cd /location/of/my/pydon/download

where /location/of/my/pydon/download is the path in your file system.

You can use a trick to get the right path, by dragging the unpacked folder onto the terminal window, so type:

    $ cd

and drag the folder there, and press return.

You can usually use tab-autocompletion to more easily find the path, i.e. type “cd “, then the first letters of the path, press tab, and the terminal will show you the possible completions, continue typing until only one option remains, and go to the next part of the path.

Rather than using the command line instructions below to unpack the two archives inside the zip (pyosc.tar.gz and XBee-2.0.1.tar.gz) you can also extract them with a graphical tool. On OSX you can just doubleclick on them to extract them.

## [step 2] : check Python version

On some operating systems python will already be installed, before you go on, check whether you have the right version:

check which version you have:
    $ python --version
If it is lower than 2.6 you will need to get a version higher than 2.6, but below version 3.

Make sure Python is in your path.

## [step 3] : Install setuptools

Setuptools is a tool to manage dependencies for Python packages, you can get it at [setuptools at pypi.python.org](http://pypi.python.org/pypi/setuptools) and find install instructions there too.

* Navigate to the extracted package
* Type:
    $ python ez_setup.py
* Or, as superuser (you’ll need to give your password)
    $ sudo python ez_setup.py

## [step 4] : Install the dependencies (from the pydon package you downloaded):

### pyOSC

    $ tar -xzvf pyosc.tar.gz
    $ cd pyosc
    $ sudo python setup.py install
    $ cd ..

`sudo` is used in order to be able to execute commands as root, rather than as user. You may be asked for your password in order to execute the command – so you will need to have administrator rights on your computer.

### XBee-2.0.1

    $ tar -xzvf XBee-2.0.1.tar.gz
    $ cd XBee-2.0.1
    $ sudo python setup.py install
    $ cd ..

### pyserial

    $ tar -xzvf pyserial.tar.gz
    $ cd pyserial
    $ sudo python setup.py install
    $ cd ..

## [step 5] : Pydon

    $ cd pydon
    $ sudo python setup.py install
    $ cd ..

For more information on python setup scripts, see the [python documentation](http://docs.python.org/install/index.html).

# Starting the program

You can now start pydongui and pydoncli from anywhere on your system:

    $ pydongui.py
    
or:

    $ pydoncli.py

# TODO

- update package contents
- update pyserial bit
- optionally include bits from common pages (w/ linux)

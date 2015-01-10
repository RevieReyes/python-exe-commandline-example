#Python Command line Executable App Example

This example evaluates the various packages that can be used to 
generate a standalone python executable App in windows.
The base of this example is a simple program that prints some text in the command line.

## Python Version

This example was tested in [`python 2.7.9`](https://www.python.org/downloads/release/python-279/) 
on an **Windows 7 64-bit based PC**.

Assuming that the Python instllation happend in he directory `C:\Python27` and 
there is a *Script Directory* at `C:\Python27\Scripts`.

## Executable conveter Packages Tested

1. [Py2Exe](http://www.py2exe.org/)
2. [cx-Freeze](http://cx-freeze.sourceforge.net/)
3. [PyInstaller](https://github.com/pyinstaller/pyinstaller/wiki)

All the above three need to configured to be able to installed to execute the individual examples.

## Environment Initialization

1. Open Command prompt using `cmd` command in *Start Menu*
2. Enter Command `SET PATH=C:\Python27;C:\Python27\Scripts;%PATH%` to 
    make sure that the `Scripts` directory is in **PATH** environment variable
    This ensures that the Path is configured properly and have access to python package manager.
3. Now for `pip` installations use the following Commands:

    `pip install cx_freeze PyInstaller virtualenv`
    
    `pip install wget` - In case one needs a download manager
    
    `pip install --upgrade cx_freeze PyInstaller virtualenv` - For upgradation

4. Download the Py2exe Installations:
    -  Installer For [64bit](http://goo.gl/teSXF8) and [32bit](http://goo.gl/Q3G5q) are available.
    -  Install any one of them depending upon the type of system Architecture. In our case it was a 64-bit one.
    -  The Package Files are located at: http://sourceforge.net/projects/py2exe/files/py2exe/ 
       In case there are any new releases of the Py2exe package
    -  We are using the [0.6.9 version of Py2exe](http://sourceforge.net/projects/py2exe/files/py2exe/0.6.9/)

5. Download the PyWin32 Installation:
    -  Installers For [64bit](http://goo.gl/Ew5uEx) and [32bit](http://goo.gl/RS7SJQ) are avaiable
    -  Install any one of them depending upon the type of system Architecture. In our case it was a 64-bit one.
    -  The Package Files are located at: 
        http://sourceforge.net/projects/pywin32/files/pywin32/ 
        In case there are any new releases of the PyWin32 package
    -  We are using the 
    [Build 219 Version of PyWin32](http://sourceforge.net/projects/pywin32/files/pywin32/Build%20219/)

With these we are ready to for creation of the executable Apps.

## cx-Freeze Procedure

This package system automatically assembles the *Distribution* package such that all the 
dependencies are take care off. The space taken by this package is the least. 
And it generate directly only one directory in the fastest process.

The command used is:

`python c:\Python27\Scripts\cxfreeze program.py -O -c --target-dir dist-cx`

In order to make this process faster we have a python file `run-cxFreeze.py`.
The command would create the `dist-cx` directory where the program executable would be created.

## PyInstaller Procedure

This package system builds the *Dependencies* and then build the *Distribution* with python + support packages.
One of the best advantage is that cross dependencies are handled very well. 

The command used is:

`pyinstaller program.py`

We have a runner program in python `run-pyinstaller.py`.
There are also `.spec` file that would be generated on the basis of default configuration.
Further advanced options can be configured by writing the `.spec` file with custom options.
Here is the Documentation Link: http://pythonhosted.org/PyInstaller/

## Py2exe Procedure

This package is the oldest of the implemntations. It works by building and then preparing the distribution.
In order to make this package work we would need a specific `setup.py` as the py2exe needes the Python distribution engine to run.

Example `setup.py`:
```python
from distutils.core import setup
import py2exe
setup(console=['program.py'])
```

The command used is:

`python setup.py py2exe`

We have both the `setup.py` and runner program `run-py2exe.py`.

## Conclusion

We have tested all the three, we found the `cx-Freeze` to be best unless 
we would need to many external modules then `PyInstaller` is better to use.

## License
This project is released in Public Domain.

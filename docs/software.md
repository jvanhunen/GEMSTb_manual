# Required software tools

## ArcGIS Pro or QGIS

Mine plan digitisation is done using GIS software. At the moment, tools are available for ArcGIS Pro or QGIS.

### ArcGIS Pro

For staff/students of Durham University, ArcGIS Pro is available through <https://appsanywhere.durham.ac.uk/login>, either in one of the computer rooms on the university campus, or on your own computer. Type your CIS username and password, and log in. An ’Open Appsanywhere’ pop-up window might appear, which you should agree to. If you are running Appsanywhere for the first time, you may be guided to install it first on your machine. In the search box, search for the latest version of `ArcGIS Pro` (version 3.0 at the time of writing), and click on `Launch Remote`. A ’Parallels Client’ remote window will open, which contains ArcGIS Pro.

ArcGIS Pro can also be directly downloaded, and, after creating an account as explained [here](https://durhamuni.maps.arcgis.com/home/index.html), can be run on your own computer, but only if your computer runs a MS Windows operating system.

### QGIS

To install the latest stable version, the user is referred to [the QGIS website](https://docs.qgis.org/3.34/en/docs/user_manual), Section 5.1.

## Python

This code requires Python 3, with Python 3.12 or 3.13 being recommended.

You can set up your environment using either Python’s built-in venv module or Conda. For Python installation, visit the official Python website at <https://python.org/downloads>.

If you prefer Conda, you can download and install it from <https://docs.conda.io/projects/conda/en/latest/user-guide/install/>. The required package list is located in the directory `config/GEMS.base.yml`. Instructions for package installation will be provided in a later section.

To check if the installation was done correctly, do the following:

- Open a terminal

- Type:  
  `which python` (MacOS or Linux)  
  `where python` (Windows)

This should provide you with a full path for the Python executable.

## Paraview

The visualisation software tool Paraview can be downloaded from <https://www.paraview.org/download/>. The Mac OS versions are all fairly stable, but the MS Windows versions not so much. If the latest version is not working properly, try installing an earlier version.

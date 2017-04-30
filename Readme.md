# Active Agenda framework and BOf::

[Active Agenda](https://sourceforge.net/projects/activeagenda) framework and [BOf::](https://activeagenda.github.io) consists of:
* [aa-base] (https://github.com/activeagenda/aa-base) - slightly modified unpublished version of [Active Agenda 0.8.2 beta] (https://github.com/activeagenda/0.8.2-beta) , used as starting point for the fork of the active agenda framework.
* [aa-patch] (https://github.com/activeagenda/aa-patch) - a patch to the  [aa-base] (https://github.com/activeagenda/aa-base) reflecting current changes to the code
* [aa-xmlbase] (https://github.com/activeagenda/aa-xmlbase) - a basic set of modules needed internally by the framework to work. It must be allways installed but can be modfied if needed
* [BOf::] (https://github.com/activeagenda/BOf) - a set of business applications developed on the basis of the fork

For an Active Agenda framework and BOf:: demo browse to http://demo-s1st.cloudapp.net Login and password are provided on the login page.

## Installation of the Active Agenda framework and BOf::
The description has been prepeared for Linux and a person having a basic knowledge of Linux, PHP, MySQL and Apache. The installation has been tested on Debian and Ubuntu 12 TLS hosted as Microsoft Azure Virtual Machine (classic).

The reference setup of [BOf::](https://activeagenda.github.io) can be downloaded as VMware virtual machine from https://www.dropbox.com The virtual machine allows interactive investigation of all configurations. 
It is strongly recommended way of investigating the framework and a sandbox for first development/admin activities.

The description assumes root access rights on a debian derivat server.

As the preparation for installation:
* Download the latest release of [aa-base] (https://github.com/activeagenda/aa-base/releases/latest) to your home directory on the server
* Unzip the downloaded file in the home directory
* Move the s2a folder from the home directory to the destination directory like  /var/www/ so that you have /var/www/s2a 
* If you have selected another destination directory that /var/www/s2a adjust the AA_PATH variable in the scripts ./s2a/util/*

##  Prerequisites
All package prerequisits are listed in the file ./s2a/util/aa-instal Run the script to install them with your prefered user/password naming philosophie

## Patch the aa-base with aa-patch
* Download [the latest aa-patch] (https://github.com/activeagenda/aa-patch/releases/latest) to ./s2a/util/ as a zip file and 
* Run the script: ./aa-patch aa-patch.X.zip
* Run ./aa-permiss to set the access permissions to files and directories  

## Patch the aa-base with aa-xmlbase
* Download the [the latest aa-xmlbase] (https://github.com/activeagenda/aa-xmlbase/releases/latest) to ./s2a/util/ as a zip file and 
* Run the script: ./aa-xml aa-xmlbase.X.zip
* Run ./aa-permiss to set the access permissions to files and directories 
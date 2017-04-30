# Active Agenda framework and BOf::

For demo browse to http://demo-s1st.cloudapp.net .Login and password are provided on the login page.

[Active Agenda](https://sourceforge.net/projects/activeagenda) framework and [BOf::](https://activeagenda.github.io) consists of:
* [aa-base](https://github.com/activeagenda/aa-base) - slightly modified unpublished version of [Active Agenda 0.8.2 beta](https://github.com/activeagenda/0.8.2-beta) , used as starting point for the fork of the active agenda framework
* [aa-patch](https://github.com/activeagenda/aa-patch) - a patch to the  [aa-base](https://github.com/activeagenda/aa-base) reflecting current changes to the code
* [aa-xmlbase](https://github.com/activeagenda/aa-xmlbase) - a basic set of modules needed internally by the framework to work. It must be always installed but can be modified if needed
* [BOf::](https://github.com/activeagenda/BOf) - a set of business applications developed on the basis of the framework

## Version numbering
The versioning numbering schema (X.X.X.X e.g. 1.1.345.23) is as follows:
* aa-base: semantic version numbering  e.g. 1.1  -> 1.1.X.X.X
* aa-patch: consecutive version numbering e.g. -> X.X.345.X
* aa-xmlbase: consecutive version numbering e.g. -> X.X.X.23

BOf:: is using consecutive version numbering and is independent  from the framework versioning.

## Installation of the Active Agenda framework and BOf::
The description has been prepared for a person having a basic knowledge of Linux, PHP, MySQL and Apache. The installation has been tested on Debian 6.0.3 squeeze and Ubuntu 12.04.05 TLS hosted as Microsoft Azure Virtual Machine (classic).

The test setup similar to [BOf::](https://activeagenda.github.io) can be downloaded as a VMware virtual machine from https://www.dropbox.com .The virtual machine allows interactive investigation of all configurations. 
It is a highly recommended way of investigating the framework and the application as well as a sandbox for first development/admin activities.

The description assumes root access rights on a debian derivate.

## Download sources
As the preparation for installation:
* Download the latest release of [aa-base](https://github.com/activeagenda/aa-base/releases/latest) to your home directory on the server
* Unzip the downloaded file in the home directory
* Move the s2a folder from the home directory to the destination directory like  /var/www/ so that you have /var/www/s2a 
* If you have selected another destination directory that /var/www/s2a adjust the AA_PATH variable in the scripts in the directory ./s2a/util/*
* Run `./aa-permiss` to set the access permissions to files and directories 

##  Package prerequisites
* All package prerequisites are listed in the aa-instal file Run `./s2a/util/aa-instal`  .Run the script to install them with your preferred root/password naming policy.
* Check php settings, see configuration file php.ini
* Check mysql settings, see configuration file
* Check appache settings, see configuration file 

## Patch the aa-base with aa-patch
* Download [the latest aa-patch](https://github.com/activeagenda/aa-patch/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch aa-patch.X.zip`

## Patch the aa-base with aa-xmlbase
* Download the [the latest aa-xmlbase](https://github.com/activeagenda/aa-xmlbase/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-xml aa-xmlbase.X.zip`

## Patch the aa-xmlbase with BOf::
* Download the [the latest BOf::](https://github.com/activeagenda/bof/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch BOf.X.zip` 

## Application auto generation
* Configure root user the database in ./s2a/active_agenda/gen-config.php (you can remove this file later, when application development is finished)
* Configure database user and password in ./s2a/active_agenda/config.php (search for "Database connection string") 
* Prepare application admin username and password requested during an interactive installation
* Run `./aa-permiss` to set the access permissions to files and directories 
* Run `./s2a/s2a.php -m mod -l pl_PL` (several runs may be needed) 
* Run `./s2a/s2a.php -t -l pl_PL` (for 460 modules 90 minutes needed)
* Run `./s2a/ s2a-install-db -u`
* Customize database root and password in ./aa-postinstall and run the script
* Configure the web server 

## Run the application
* Browse to the application and login in
* Enter new people (URL bar: .../list.php?mdl=ppl) and make out of them user (URL bar: .../list.php?mdl=ppl) with proper modules permissions

## Email notfication setup
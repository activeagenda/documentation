# Installation of the framework and BOf ::
The description has been prepared for a person having a basic knowledge of Linux, PHP, MySQL and Apache. The installation has been tested on Debian 6.0.3 squeeze and Ubuntu 12.04.05 TLS hosted as "Microsoft Azure Virtual Machine (classic)".

The test setup similar to [BOf::](https://activeagenda.github.io) can be downloaded as a VMware virtual machine from https://www.dropbox.com .The virtual machine allows interactive investigation of all configurations. 
It is a highly recommended way of investigating the framework and the application as well as a sandbox for first development/admin activities.

The description assumes root access rights on a debian derivate.

## Download sources
As the preparation for installation:
* Download [the latest release of aa-base](https://github.com/activeagenda/aa-base/releases/latest) to your home directory on the server
* Unpack the downloaded file in the home directory of your server
* Move the s2a folder from the home directory to the destination directory like  /var/www/ so that you have /var/www/s2a 
* If you have selected another destination directory that /var/www/s2a adjust the AA_PATH variable in the scripts in the directory ./s2a/util/*
* Set root root permissions and run `./aa-permiss` to set the access permissions to files and directories 

##  Install framework prerequisites
* All package prerequisites are listed in the aa-instal file Run `./s2a/util/aa-install`. Run the script to install them with your preferred root/password naming policy.
* Create by coping the file gd.ini to  /etc/php5/conf.d/cairo.ini with content `extension=cairo.so`
* Check php settings for Apache, see configuration file [php.ini](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/php.ini)
* Check php settings for CLI are set `memory_limit=64M` (Ubuntu 12.04.1 TLS default `memory_limit=-1` prevents execution of bigger php scripts) 
* Check mysql settings, see configuration file [my.cnf](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/my.cnf)
* Execute a2enmod  for  /etc/apache2/mods-available:
  * expires.load 
  * headers.load 
* Configure Google mod_pagespeed: 
  * Set: ModPagespeedRewritwLevel PassTrough 
  * Uncomment: ModPagespeedEnableFilters=*
* Set in /etc/apache2/conf.d/charset: AddDefaultCharset UTF-8
* Adjust the apache site configuartion  [/etc/apache2/sites-avaiable/default](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/default)
* Enable site with the command `a2ensite default`

## Patch the aa-base with aa-patch
* Download [the latest release of aa-patch](https://github.com/activeagenda/aa-patch/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch aa-patch-X.zip`

## Patch the aa-base with aa-xmlbase
* Download the [the latest release of aa-xmlbase](https://github.com/activeagenda/aa-xmlbase/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-xmlbase aa-xmlbase-X.zip`

## Patch the aa-base with tutor
* Download the [the latest release of aa-xmlbase](https://github.com/activeagenda/tutor/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch tutor-X.zip`

## Patch the aa-xmlbase with BOf ::
* Download the [the latest release of BOf::](https://github.com/activeagenda/bof/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch BOf-X.zip` 

## Application auto generation
* Configure root database user the  in ./s2a/active_agenda/[gen-config.php](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/gen-config.php) (you can remove this file later, when application development is finished)
* Configure database user and password in ./s2a/active_agenda/[config.php](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/config.php) (search for "Database connection string") 
* Prepare application admin username and password requested during an interactive installation
* Run `./aa-permiss` to set the access permissions to files and directories 
* Run `./s2a/php s2a-install-db.php` (set "activeagenda" as database name) 
* Run `./s2a/s2a.php -t -l pl_PL` (be prepared to enter database root password, do not be upset by error lines - the genrator traverses a tree of dependencies, the generation may take several minutes)
* Run `./s2a/s2a.php -m % -l pl_PL -rp your_db_password` to verify the generation, look at the end of the execution for the line: "Requieres confirmation: 0; Failed 0"
* Run `./s2a/util/aa-postinstall` (installs dictionaries need bz the modules)
* Run `./s2a/ s2a-install-db -u` (application admin username and password)
* Customize database root and password in the file ./aa-postinstall, run the script `./aa-postinstall`
* Configure the web server 

## Test the application installation
* Browse to the application and login in with the credentials entered during autogeneration
* Enter new people (browser URL bar: .../list.php?mdl=ppl) and make out of them user (browser URL bar: .../list.php?mdl=ppl) with proper modules permissions
* Play a bit with the application ...

## Email notfication setup
* Configure ./s2a/active_agenda/[email-config.php](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/email-config.php) 
* Setup crone job, see the [cron job](https://github.com/activeagenda/documentation/blob/master/1%20%20Framework%20and%20BOf%20installation/config%20file%20examples/cronjob)
* Setup email connection to your main post server your prefered way

## Feedback
https://github.com/activeagenda/bof/issues 
#  BOf :: on Active Agenda framework

## Demo
For demo browse to http://demo-s1st.cloudapp.net .Login and password are provided on the login page.

## Framework structure
[Active Agenda](https://sourceforge.net/projects/activeagenda) framework and [BOf ::](https://activeagenda.github.io) consists of:
* [aa-base](https://github.com/activeagenda/aa-base) - slightly modified unpublished version of [Active Agenda 0.8.2 beta](https://github.com/activeagenda/0.8.2-beta) , starting point for the fork of the active agenda framework
* [aa-patch](https://github.com/activeagenda/aa-patch) - a patch to the  [aa-base](https://github.com/activeagenda/aa-base) reflecting development changes to the code
* [aa-xmlbase](https://github.com/activeagenda/aa-xmlbase) - a basic set of modules needed by the framework to work. It must be always installed but can be modified if needed
* [BOf ::](https://github.com/activeagenda/BOf) - a set of business applications developed on the basis of the framework

## Release numbering
The release versioning numbering schema (X.X.X.X e.g. 1.1.345.23) is as follows:
* aa-base: semantic version numbering  e.g. 1.1  -> 1.1.X.X.X
* aa-patch: consecutive version numbering e.g. -> X.X.345.X
* aa-xmlbase: consecutive version numbering e.g. -> X.X.X.23

BOf:: is using consecutive version release numbering. The schema is independent  from the framework versioning.

## Installation of the framework and BOf ::
The description has been prepared for a person having a basic knowledge of Linux, PHP, MySQL and Apache. The installation has been tested on Debian 6.0.3 squeeze and Ubuntu 12.04.05 TLS hosted as "Microsoft Azure Virtual Machine (classic)".

The test setup similar to [BOf::](https://activeagenda.github.io) can be downloaded as a VMware virtual machine from https://www.dropbox.com .The virtual machine allows interactive investigation of all configurations. 
It is a highly recommended way of investigating the framework and the application as well as a sandbox for first development/admin activities.

The description assumes root access rights on a debian derivate.

### Download sources
As the preparation for installation:
* Download [the latest release of aa-base](https://github.com/activeagenda/aa-base/releases/latest) to your home directory on the server
* Unzip the downloaded file in the home directory
* Move the s2a folder from the home directory to the destination directory like  /var/www/ so that you have /var/www/s2a 
* If you have selected another destination directory that /var/www/s2a adjust the AA_PATH variable in the scripts in the directory ./s2a/util/*
* Run `./aa-permiss` to set the access permissions to files and directories 

###  Install framework prerequisites
* All package prerequisites are listed in the aa-instal file Run `./s2a/util/aa-install`  .Run the script to install them with your preferred root/password naming policy.
* Check php settings, see configuration file [php.ini](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/php.ini)
* Check mysql settings, see configuration file [my.cnf](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/my.cnf)
* Check appache settings, see configuration file [default](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/default)

### Patch the aa-base with aa-patch
* Download [the latest release of aa-patch](https://github.com/activeagenda/aa-patch/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch aa-patch.X.zip`

### Patch the aa-base with aa-xmlbase
* Download the [the latest release of aa-xmlbase](https://github.com/activeagenda/aa-xmlbase/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-xml aa-xmlbase.X.zip`

### Patch the aa-xmlbase with BOf ::
* Download the [the latest release of BOf::](https://github.com/activeagenda/bof/releases/latest) to directory ./s2a/util/ as a zip file
* Run the script: `./aa-patch BOf.X.zip` 

### Application auto generation
* Configure root database user the  in ./s2a/active_agenda/[gen-config.php](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/gen-config.php) (you can remove this file later, when application development is finished)
* Configure database user and password in ./s2a/active_agenda/[config.php](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/config.php) (search for "Database connection string") 
* Prepare application admin username and password requested during an interactive installation
* Run `./aa-permiss` to set the access permissions to files and directories 
* Run `./s2a/s2a.php -m mod -l pl_PL` (try several times if error encountered 
* Run `./s2a/s2a.php -t -l pl_PL` (Beware of generation time - several minutes needed)
* Run `./s2a/ s2a-install-db -u`
* Customize database root and password in the file ./aa-postinstall and run the script `./aa-postinstall`
* Configure the web server 

### Test the application installation
* Browse to the application and login in with the credentials entered during autogeneration
* Enter new people (Browser URL bar: .../list.php?mdl=ppl) and make out of them user (Browser URL bar: .../list.php?mdl=ppl) with proper modules permissions
* Play a bit with the application ...

### Email notfication setup
* Configure ./s2a/active_agenda/[email-config.php](https://github.com/activeagenda/documentation/blob/master/config%20file%20examples/email-config.php) 
* Setup crone job
* Setup email connection to your post server

## Feedback
https://github.com/activeagenda/bof/issues 
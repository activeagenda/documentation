#  BOf :: on Active Agenda framework

## Demo
For demo browse to http://demo-s1st.cloudapp.net .Login and password are provided on the login page.

## Framework structure
[Active Agenda](https://sourceforge.net/projects/activeagenda) framework and [BOf ::](https://activeagenda.github.io) consists of:
* [aa-base](https://github.com/activeagenda/aa-base) - slightly modified unpublished version of [Active Agenda 0.8.2 beta](https://github.com/activeagenda/0.8.2-beta) , starting point for the fork of the active agenda framework
* [aa-patch](https://github.com/activeagenda/aa-patch) - a patch to the  [aa-base](https://github.com/activeagenda/aa-base) reflecting development changes to the code
* [aa-xmlbase](https://github.com/activeagenda/aa-xmlbase) - a basic set of modules needed by the framework to work. It must be always installed but can be modified if needed
* [BOf ::](https://github.com/activeagenda/BOf) - a set of business modules developed on the basis of the framework

## Framework release numbering
The release versioning numbering schema (X.X.X e.g. 1.345.23) is as follows:
* aa-base: semantic version numbering  e.g. 1  -> 1.X.X
* aa-patch: consecutive version numbering e.g. -> X.345.X
* aa-xmlbase: consecutive version numbering e.g. -> X.X.23

## BOf :: release numbering
BOf:: is using consecutive version release numbering. The schema is independent  from the framework versioning.

## Documentation
For instructions on framework installation, BOf :: implementation and module development browse the content of folders in this directory.
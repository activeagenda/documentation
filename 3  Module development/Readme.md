# Documentation
For module development documenation browse to [Active Agenda - The Technology](http://www.activeagenda.com/tiki-index.php?page=The%20Technology) The legacy documentation is stored in the folder [Active Agenda 0.8.2-beta Technology documentation](https://github.com/activeagenda/documentation/tree/master/3%20%20Module%20development/Active%20Agenda%200.8.2-beta%20Technology%20documention)

Changes are documented in "Technology Notices" in the polish language. [Use Google Translate for browsing the files](https://translate.googleusercontent.com/translate_c?act=url&depth=1&hl=en&ie=UTF8&prev=_t&rurl=translate.google.co.uk&sl=pl&sp=nmt4&tl=en&u=https://github.com/activeagenda/documentation/tree/master/3%2520%2520Module%2520development/Technology%2520Notices&usg=ALkJrhiJZO-asAW_c10QufCQVlMNrwz7cg){:target="_blank"}

# Module auto generation
Look inside the script ./s2a/uti/[aa-exco](https://github.com/activeagenda/aa-base/blob/master/s2a/util/aa-exco) for actiities needed to auto generate a module.

# Notepad++ integration
For development using local installed virtula machine and working Putty connection to the virtual machine assumed, save in Notepad++ "/Plugins/NppExec/Execut ... F6" as "BOf".
```bash
SET COMPILE_MODULES = xat
SET AA_HOST = 192.168.178.22
SET ROOT_PASSWORD = swords
SET DB_PASSWORD = swords

7z a -w -tzip  -xr!.*  "$(CURRENT_DIRECTORY).zip" "$(CURRENT_DIRECTORY)"
pscp -pw $(ROOT_PASSWORD) "$(CURRENT_DIRECTORY).zip" root@$(AA_HOST):/var/www/s2a/util
plink -pw $(ROOT_PASSWORD)  root@$(AA_HOST) /var/www/s2a/util/aa-exco '$(DB_PASSWORD)' '$(CURRENT_DIRECTORY)' '$(COMPILE_MODULES)'
``` 
# ibnr-conf
This is the config file that is consumed by bnr's bnr script.

## Format

#### Sample Entry 1 ####
`emacs "init.el" 0:0 ~/".emacs.d/init.el"`  

#### Sample Entry 2 ####
`$def$-unity unity.conf 0:1 !`  
  
  There are 4 columns in this file. Each column *should* hold a value or have ! to indicate no value.
  1. Program Name - This is the name that identifies the software. Values for this column that begin with `$def$` in a `-` separated value are processed irrespective of whether a matching value is present in the provided install log file.  
     Example: The [Sample Entry 2](https://github.com/wrvenkat/bnr-conf#sample-entry-2) line will be processed always.
  2. Backup File Name - This is the name that will be used to store the dotfile contents.
  3. Properties - Colon (:) separated tuple, that identifies the following properties for the entry,
	 1. Super user flag - if 1, indicates whether super user access is required to copy the file into the destination.
	 2. Config script flag - if 1, indicates whether there is a separate script that needs to be run to create or restore a backup. The corresponding scripts are located in the [config_scripts](https://github.com/wrvenkat/config_scripts) directory and are identified by appending `-bnr.sh` to the Program Name column value.  
		Example: The [Sample Entry 2](https://github.com/wrvenkat/bnr-conf#sample-entry-2) line indicates that it requires a script to be executed. This script is identified by the name `$def$-unity-bnr.sh` inside the config_scripts directory.
  4. Source File Name - The destination path for the dotfile. Values specified within double quotes are taken literallya and double quotes need to be escaped with a backslash. The bnr script performs [tilde-expansion](https://github.com/wrvenkat/bash_helper_scripts#safe_tilde_expansionsh) on the value for this column. The values are similar to regular bash file path.  
	 Example: The [Sample Entry 1](https://github.com/wrvenkat/bnr-conf#sample-entry-1) refers to the dotfile location with a tilde-prefixed file path.
  
Generally, any text enclosed within double quotes are taken literally.

## Getting Started
  * You are encouraged to customize the config file according to your needs.
  * All column values should either have an entry or have ! as a place holder value.
  * All enabled entries in a particular version have been tested on that version of Ubuntu.
  * Any part of a line starting with a # is considered as a comment and is ignored. So, if you don't need a line to be processed, you can simply disable it by commenting it out.
  * If you want to contribute, you can do so by contributing entries alone or if the backup and restore requires a script, the entry and the corresponding script. For more information on this and on how bnr calls the config scripts, please see [config_scripts](https://github.com/wrvenkat/config_scripts).

## Versioning ##
  * Master branch is the main development branch and the head should have the stable version.

## LICENSE

[GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html)

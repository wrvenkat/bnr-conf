# ibnr-conf
This is the config file that is consumed by bnr's bnr script.

## Format

#### Sample Entry 1 ####
`tlp "tlp" 1:0 "/etc/default/tlp"`  

#### Sample Entry 2 ####
`$def$-unity unity.conf 0:1 !`  
  
  There are 4 columns in this file. Each column *should* hold a value or have ! to indicate no value.
  1. Program Name - This is the name that identifies the software. Values for this column that begin with `$def$` in a `-` separated value indicate that this line needs to be processed irrespective of whether a matching value is present in the provided install log file.  
     Example: The [Sample Entry 2](https://github.com/wrvenkat/bnr-conf#sample-entry-2) line will be processed always.
  2. Backup File Name - This is the name that will be used to store the dotfile contents.
  3. Properties - Colon (:) separated tuple, that identifies the following properties for the entry,
	 1. First flag - if 1, indicates whether super user access required to copy the file into the destination.
	 2. Second flag - if 1, indicates whether there is a separate script that needs to be run to create or restore a backup.
  4. Source File Name - The destination path for the dotfile. Values specified within double quotes are taken literally. Double quotes need to be escaped with a backslash. The bnr script performs tilde-expansion on the value for this column.
  
  Generally, any text enclosed within double quotes are taken literally.

## Getting Started
  * You are encouraged to customize the config file according to your needs. All entries are available to be installed when a file is checked out from the repository.
  * All column values should either have an entry or have ! as a place holder value.
  * All enabled entries in a particular version have been tested on that version of Ubuntu.
  * Any part of a line starting with a # is considered as a comment and is ignored. So, if you don't need a software to be installed, you can simply disable it by commenting it out.
  * The install script checks whether a PPA already exists or not before adding it.
  * If you want to contribute, you can do so by contributing entries alone or if the installation requires a script, the entry and the corresponding install script. For more information on this, please see [install_scripts](https://github.com/wrvenkat/install_scripts).

## Versioning ##
  * Stable versions are organized along the lines of Ubuntu version numbers - 14.04, 16.04 etc.
  * Master branch is the main development branch and test branch is where main testing goes on before being merged into stable versions.
  * There are no test branches for corresponding stable branches.
  * Branching model requires revision.

## LICENSE

[GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html)

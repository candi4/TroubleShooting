# Ubuntu_server
How to control ubuntu server with command

## Ubuntu commands
### Make directory
```
mkdir directory1
```
### Remove file/directory
```
rm filename.exe
rm -r directory1
```
* -f: Forces the removal of all files or directories.
* -i: Prompts for confirmation before removing.
* -I: Prompts once before removing more than three files or when removing recursively.
* -r: Removes directories and their content recursively.
* -d: Removes empty directories.
* -v: Provides a verbose output.
* --help: Displays the help text.
* --version: Displays the command version.
### Move file/directory 
```
mv [PATH/]src [PATH/]dest
```
* Move [PATH/]src into [PATH/]dest
### Download from internet
```
wget Web_Addresses
```
### Unzip
```
unzip compressed.zip
```
### Get current path
```
pwd
```
### Check GPUs in use in realtime
```
gpustat --watch
```
## Communication with Ubuntu server
### Send file
```
scp [options] [source] [target]
```
* From remote to local (Remote -> Local)    
  Should be run in local
    ```shell
    # One file
    scp username@123.456.789.012:[source] [target]
    # All files in the directory
    scp username@123.456.789.012:[sourcedir]/* [target]
    # All files including subdirectories
    scp -r username@123.456.789.012:[sourcedir]/* [target]
    ```
* From local to remote (Local -> Remote)    
  Should be run in local
    ```shell
    scp [source] username@123.456.789.012:[target]
    ```

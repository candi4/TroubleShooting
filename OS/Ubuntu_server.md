# Ubuntu_server
How to control ubuntu server with command

## Ubuntu commands
### Make directory
```shell
mkdir directory1
# multiple directories
mkdir dir1 dir2
mkdir d{1,2}
mkdir -p directory{1..3}/sub{01..10} # 30 directories
mkdir dir_{a-z} # 26 directories
```
* `-p` : Makes parent directories as needed.

References:
* [Is there a way to create multiple directories at once with mkdir?](https://askubuntu.com/questions/731721/is-there-a-way-to-create-multiple-directories-at-once-with-mkdir)
### Create a file
```shell
touch test.txt
nano nonexistfile.txt # You can create and revise a file simulatenously.
```
Reference: [How to Create a File in Linux](https://phoenixnap.com/kb/how-to-create-a-file-in-linux)
### Remove file/directory
```shell
rm filename.exe
rm -r directory1
```
* `-f` : Forces the removal of all files or directories.
* `-i` : Prompts for confirmation before removing.
* `-I` : Prompts once before removing more than three files or when removing recursively.
* `-r` : Removes directories and their content recursively.
* `-d` : Removes empty directories.
* `-v` : Provides a verbose output.
* `--help` : Displays the help text.
* `--version` : Displays the command version.
### Move file/directory 
```shell
mv [PATH/]src [PATH/]dest
```
* Move [PATH/]src into [PATH/]dest
### Copy file
```shell
cp [PATH/]src [PATH/]dest
cp -r src/ dest/
```
* Copy [PATH/]src into [PATH/]dest
### Download from internet
```shell
wget Web_Addresses
```
### Unzip
```shell
unzip compressed.zip
```
### Get current path
```shell
pwd
```
### Check GPUs in use in realtime
```shell
gpustat --watch
```
### Check users using GPU server
```shell
who
```
### Check which server (IP) I am using
```shell
hostname -I
wget -qO- ifconfig.co
```
Reference: [find out external ip and use to access ssh server](https://askubuntu.com/questions/1248598/find-out-external-ip-and-use-to-access-ssh-server)

## Communication with Ubuntu server
### Send file
Copies `source` and pastes it in `target`.
```shell
scp [options] [source] [target]
```
* `-r` : Copies and pastes directories and their content recursively.
* `-rf` : May not work.

Examples
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

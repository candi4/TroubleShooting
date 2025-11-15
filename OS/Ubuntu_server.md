# Ubuntu_server
How to control ubuntu server with command






## Active commands

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

### Save output to file
These aren't compatible with tqdm in python. Refer to `taceback` module of python.
```shell
python code.py > log.txt 2>&1 # Saves output without displaying
python code.py 2>&1 | tee log.txt # Displays and saves output
```
* `2>&1`: include error message

### Kill python process
Find the process ID (PID) first, then kill it.
```shell
ps aux | grep python
```
The second column shows the process ID (PID).
```
hojun     12345  0.5  2.1 123456 87654 pts/0  Sl+  09:15   0:10 python train.py
```
```shell
kill 12345
kill -9 12345
```







## Passive commands

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
who am i # Check which one is me
```


### Check which server (IP) I am using
```shell
hostname -I
wget -qO- ifconfig.co
```
Reference: [find out external ip and use to access ssh server](https://askubuntu.com/questions/1248598/find-out-external-ip-and-use-to-access-ssh-server)


### Check CPU
```shell
lscpu
```
* `Socket(s)`: Number of physical CPUs on the motherboard
* `Core(s) per socket`: Physical cores per CPU
  * Total physical cores = `Socket(s)` * `Core(s) per socket` (Parallel process)


### Check ubuntu version
```shell
lsb_release -a
```

### Check command line of running processes
```shell
pgrep -af "python train.py "
```
It shows the process ID and the full command line of all processes matching the pattern "python train.py".


### Find a file
```shell
find . -name "config.py"
```







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

### tmux (Editing)
```shell
sudo apt install tmux
```
```shell
tmux new -s <session_name> # Create a new session
tmux ls # List all sessions
tmux attach -t <session_name> # Attach to a session
```
* `ctrl + b + %` : Split the window vertically
* `ctrl + b + "` : Split the window horizontally
* `ctrl + b + arrow key` : Move between panes
* `ctrl + b + [` : Enter copy mode to scroll through the output (quit with `q`)

* `ctrl + b + :` + `resize-pane -D [size]` : Resize the current pane down
* `ctrl + b + :` + `resize-pane -U [size]` : Resize the current pane up
* `ctrl + b + :` + `resize-pane -L [size]` : Resize the current pane left
* `ctrl + b + :` + `resize-pane -R [size]` : Resize the current pane right

* simultaneously typeing in all panes:
  * `ctrl + b + :` + `setw synchronize-panes on` : Enable
  * `ctrl + b + :` + `setw synchronize-panes off` : Disable

* References
* [[Linux] tmux를 사용해보자](https://velog.io/@piopiop/Linux-tmux%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EC%9E%90)
* [Tmux (Terminal multiplexer) 사용법](https://m.blog.naver.com/PostView.naver?blogId=songsite123&logNo=223809804101&navType=by) (Detail)
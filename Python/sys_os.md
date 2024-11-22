# sys_os
Issues about the module sys and os

## Handle path string
### Add environment variable
```python
# <current_directory>/../
sys.path.insert(0, os.path.dirname(os.path.abspath(__file__))+"/../")
```
### Get directory of the file
```python
os.path.dirname(filename)
```
* directory1/directory2/file.exe -> directory1/directory2    
* directory1/directory2/file -> directory1/directory2    
* directory1/directory2/ -> directory1/directory2    
### Check existance of the directory or the file
```python
os.path.exists(filename)
os.path.exists(dirname)
os.path.exists(os.path.dirname(filename))
```
### Split extention of a filename
```python
filename, file_extension = os.path.splitext(path)
```
* `'/path/to/somefile.ext'` -> `('/path/to/somefile','.ext')`
* `'/a/b.c/d'` -> `('/a/b.c/d', '')`
* References
    * [Extracting extension from filename in Python](https://stackoverflow.com/questions/541390/extracting-extension-from-filename-in-python)
## Combine directories
```python
os.path.join("/A/B/C", "file.py") # '/A/B/C/file.py'
```
## Manage files and directories
### Make directories (mkdir)
```python
os.makedirs("dir1/dir2", exist_ok=True)
```
* If `exist_ok=False`, an error occurs if the directory already exists. The default value is `False`.
### Get subpaths
```python
# Direct subpaths (subfiles and subdirectories)
subpath_list = os.listdir('dir1')
```
* `subpath_list = ['dir2', 'file2.txt', 'file3.txt']` with follow paths:
    * `dir1/dir2/file1.txt`
    * `dir1/file2.txt`
    * `dir1/file3.txt`
```python
# Only direct subfiles 
file_list = [path for path in os.listdir(directory) if os.path.isfile(f"{directory}/{path}")]
```
### Delete files
```python
import shutil
shutil.rmtree(dir_path) # deletes a directory and all its contents.
```
[How can I delete a file or folder in Python?](https://stackoverflow.com/questions/6996603/how-can-i-delete-a-file-or-folder-in-python)
### Move a file
Move one file `src` to `dst`. `dst` is a filename.
```python
os.rename(src, dst)
os.replace(src, dst)
shutil.move(src, dst)
```
[How do I move a file in Python?](https://stackoverflow.com/questions/8858008/how-do-i-move-a-file-in-python)
### Copy files
```python
shutil.copy(src, dst)
```
[shutil — High-level file operations #shutil.copy](https://docs.python.org/ko/3/library/shutil.html#shutil.copy)
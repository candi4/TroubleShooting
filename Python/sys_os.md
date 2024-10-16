# sys_os
Issues about the module sys and os

## Usages
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
### Make directories
```python
os.makedirs("dir1/dir2", exist_ok=True)
```
* If `exist_ok=False`, an error occurs if the directory already exists. The default value is `False`.

# sys_os
Issues about the module sys and os

## Usages
### Add environment variable
```
# <current_directory>/../
sys.path.insert(0, os.path.dirname(os.path.abspath(__file__))+"/../")
```
### Get directory of the file
```
os.path.dirname(filename)
```
* directory1/directory2/file.exe -> directory1/directory2    
* directory1/directory2/file -> directory1/directory2    
* directory1/directory2/ -> directory1/directory2    

# sys_os
Issues about the module sys and os

## Usages
### Add environment variable
```
# <current_directory>/../
sys.path.insert(0, os.path.dirname(os.path.abspath(__file__))+"/../")
```
# TroubleShooting/Git
Troubleshooting issues related to Git and GitHub.

## git repository not found
### Error:
```
> git push origin main:main
remote: Repository not found.
fatal: repository 'https://github.com/KHJ273/EV_charging_robot.git/' not found
```
It's because the repository is private.    
### Resolve:
```
$ git remote set-url origin https://KHJ273@github.com/KHJ273/EV_charging_robot.git/
```

## Prune not existing branches
```
git fetch --prune
```

## .gitignore
Add List in .gitignore to be ignored when using git push
```
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
```
### References
* [GitHub gitignore/Python.gitignore](https://github.com/github/gitignore/blob/main/Python.gitignore)

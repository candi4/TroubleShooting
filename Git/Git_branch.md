# TroubleShooting/Git
Troubleshooting issues related to Git and GitHub.

## Clone private repository
```
git clone https://KHJ273@github.com/KHJ273/EV_charging_robot.git

cd EV_charging_robot
git checkout origin/main
git branch
```
### Another way
1. Change directory into one be used as root
2. Initialize git to use the directory as root
    ```
    git init
    ```
3. Add remote
    ```
    git remote add origin https://KHJ273@github.com/KHJ273/EV_charging_robot.git
    ```
4. Refresh all remote branches
    ```
    git remote update
    ```
    * `git fetch` is for a specific remote
5. Check remote branches
    ```
    git branch -r
    ```
6. Switch to the wanted branch
    ```
    git checkout origin/main
    ```
7. Check the current branch and the file list
    ```
    git branch
    ls
    ```

## Prune non-existing remote branches
```
git fetch --prune
```

## Get the commit id (branch hash)
```
git rev-parse <branch name>
git rev-parse HEAD
git log
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

## Revert pushed commit
* Using command
    ```shell
    git log 
    git revert --no-commit HEAD~3.. # three steps ago
    git commit -m <message>
    git push <remote> <branch>
    ```
* Using vscode
    1. See gitgraph
    2. Right-click on the commit
    3. Click `Revert`
### References
* [원격저장소에 올라간 git commit 되돌리기](https://simple-ing.tistory.com/60)
# GitHub Authorization
How to use GitHub login for Git commands.

## GitHub CLI
### Install GitHub CLI
```shell
conda install -c conda-forge gh
```
Check installation:
```shell
gh --version
```

### Login to GitHub
Use browser login, not manual token input.
```shell
gh auth login
```
Recommended choices:
```text
GitHub.com
HTTPS
Yes, authenticate Git with your GitHub credentials
Login with a web browser
```
If the prompt stops or does not continue, use this command instead:
```shell
gh auth login --hostname github.com --git-protocol https --web
```
Open the given URL in your local browser and enter the one-time code.

### Let Git use gh login
```shell
gh auth setup-git
```
This makes `git push`, `git pull`, and `git clone` use the GitHub login saved by `gh`.

### Check status
```shell
gh auth status
git config --global --get-all credential.helper
```

### Logout
Use this when you want to remove GitHub login from the server.
```shell
gh auth logout
```
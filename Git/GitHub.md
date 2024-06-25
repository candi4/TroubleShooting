# TroubleShooting/Git
Troubleshooting issues related to Git and GitHub.

## git repository not found
### Error:
```
> git push origin main:main
remote: Repository not found.
fatal: repository 'https://github.com/KHJ273/EV_charging_robot.git/' not found
```
### Resolve:
```
$ git remote set-url origin https://KHJ273@github.com/KHJ273/EV_charging_robot.git/
```

# Set_Ubuntu

## Install Hangul
1. `sudo apt update` 
2. `sudo apt upgrade ibus-hangul -y` 
3. Reboot.
4. settings ➔ Region & Language
5. Add `Korean (Hangul)` to input sources.
6. Enter `Korean (Hangul)` settings 
7. Configure the Hangul toggle key.
8. Delete `English (US)`.


## Manage the delay of repeating keys
Settings ➔ universal access ➔ typing ➔ repeat keys ➔ Adjust delay
## (laptop) Keep the screen from turning off when closed
sudo vi /etc/systemd/logind.conf > 수정을 위해 i를 누른다 > #HandleLidSwitch=suspend 를 HandleLidSwitch=ignore 로 바꾼다 > ESC 버튼을 누른 후 :wq를 눌러 저장한다. > 다음을 입력하여 서비스 재시작 sudo service systemd-logind restart
## Prevent the screen from turning off over time
Settings ➔ Power ➔ Black screen ➔ Never


## Additional Install
### terminator
```
sudo apt install terminator
```
[Show only one instance of Terminator in the favorite dock](https://askubuntu.com/questions/1242536/ubuntu-dock-adds-a-new-icon-when-i-open-certain-programs)
### Etc
chrome, vscode
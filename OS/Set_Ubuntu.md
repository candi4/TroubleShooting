# Set_Ubuntu

## Contents
### Install Hangul
터미널에서 sudo apt update > sudo apt upgrade ibus-hangul -y > reboot > 설정에 region & language 들어가서 input sources에 Korean(Hangul) 추가함. Korean(Hangul) 설정 들어가서 한글토글키 설정하기.
### Manage the delay of repeating keys
설정 > universal access > typing > repeat keys > delay 조절
### Keep the laptop screen from turning off when closed
sudo vi /etc/systemd/logind.conf > 수정을 위해 i를 누른다 > #HandleLidSwitch=suspend 를 HandleLidSwitch=ignore 로 바꾼다 > ESC 버튼을 누른 후 :wq를 눌러 저장한다. > 다음을 입력하여 서비스 재시작 sudo service systemd-logind restart
### Prevent the screen from turning off over time
우측상단 설정 > Power > Black screen 
### Show only one instance of Terminator in the favorite dock
https://askubuntu.com/questions/1242536/ubuntu-dock-adds-a-new-icon-when-i-open-certain-programs

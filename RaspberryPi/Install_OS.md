# Install_OS

## Install Ubuntu server in Raspberry Pi

* 노트북에 라즈베리파이 imager 설치 및 실행. 
* 노트북에 sd카드 장착(기존에 다른 os가 설치된 저장소면 운영체제 선택에서 삭제 버튼으로 초기화(파티션 나뉜것도 합쳐짐)해주고 sd카드 다시 장착)
* 운영체제 선택 -> Other general-purpose OS -> Ubuntu -> Ubuntu Server 22.04.2 LTS (64-bit) 선택 (server는 GUI 없고 desktop은 있음.) (우분투 desktop버전은 미리 LAN설정 등 안돼서 모니터 필요. 서버 설치 후 데스크탑 설치할 것임.) (라즈베리파이OS는 ROS 설치가 어려워서 포기.)
* -> 저장소 선택 -> 빈 sd 카드 선택
* -> 설정(톱니모양) -> 여러 설정.(노트북과 연결 위해서 필수 : SSH 사용(비밀번호 인증 사용) 선택, 사용자 이름 및 비밀번호 설정, 무선 LAN 설정은 노트북 핫스팟으로) -> 저장
* -> 쓰기(SD카드에 OS 이미지를 입혀줌.) -> 예 -> 완료될때까지 대기. -> 완료된 후 sd카드 제거
* -> SD카드를 라즈베리파이에 꽂고 모니터 연결 후 전원 연결. -> 2분이 지나도록 와이파이가 연결되지 않으면 라즈베리파이 전원 껐다가 다시 키기.
* -> (노트북 연결 등으로 터미널 쓸 수 있게 되면 desktop environment 설치하기) sudo apt update -> sudo apt upgrade -> sudo reboot -> sudo apt install ubuntu-desktop -> sudo reboot

## Reference
* [라즈베리파이 Raspberry Pi OS 설치 및 간단 설정 방법 (Raspberry Pi Imager 1.7.3)](https://blog.naver.com/kbc20000/222997275244)
* [Raspberry Pi Imager installation files (Windows) ](https://downloads.raspberrypi.org/imager/) # imager_1.8.5.exe
* [Ubuntu server version -> desktop version](https://roboticsbackend.com/install-ubuntu-on-raspberry-pi-without-monitor/)

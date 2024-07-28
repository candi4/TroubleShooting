# Install_OS

## Install Ubuntu server in Raspberry Pi

* 노트북에 라즈베리파이 imager 설치 및 실행. 
* 노트북에 sd카드 장착(기존에 다른 os가 설치된 저장소면 운영체제 선택에서 삭제 버튼으로 초기화(파티션 나뉜것도 합쳐짐)해주고 sd카드 다시 장착)
* 운영체제 선택 -> Other general-purpose OS -> Ubuntu -> Ubuntu Server 22.04.2 LTS (64-bit) 선택 (server는 GUI 없고 desktop은 있음.) (우분투 desktop버전은 미리 LAN설정 등 안돼서 모니터 필요. 서버 설치 후 데스크탑 설치할 것임.) (라즈베리파이OS는 ROS 설치가 어려워서 포기.)
* -> 저장소 선택 -> 빈 sd 카드 선택
* -> 설정(톱니모양) -> 여러 설정.(노트북과 연결 위해서 필수 : SSH 사용(비밀번호 인증 사용) 선택, 사용자 이름 및 비밀번호 설정, 무선 LAN 설정은 노트북 핫스팟으로) -> 저장
* -> 쓰기(SD카드에 OS 이미지를 입혀줌.) -> 예 -> 완료될때까지 대기. -> 완료된 후 sd카드 제거
* -> SD카드를 라즈베리파이에 꽂고 전원 연결. -> 2분이 지나도록 와이파이가 연결되지 않으면 라즈베리파이 전원 껐다가 다시 키기.
* -> (노트북 연결 등으로 터미널 쓸 수 있게 되면 desktop environment 설치하기) 

### References
* [라즈베리파이 Raspberry Pi OS 설치 및 간단 설정 방법 (Raspberry Pi Imager 1.7.3)](https://blog.naver.com/kbc20000/222997275244)
* [Raspberry Pi Imager installation files (Windows) ](https://downloads.raspberrypi.org/imager/) # imager_1.8.5.exe
* [Ubuntu server version -> desktop version](https://roboticsbackend.com/install-ubuntu-on-raspberry-pi-without-monitor/)

## Settings in Raspberry Pi imager (for connection with laptop)
* hostname 설정
* SSH 사용 : 비밀번호 인증 사용
* 사용자 이름
* 비밀번호
* 무선 LAN 설정. (노트북 핫스팟)
* 로케일 설정 지정. 시간대 : Asia/Seoul , 키보드 레이아웃 : kr


## Connect with laptop
1. SSH (remote connection)    
라즈베리파이 실행(노트북 핫스팟에 자동 연결) -> putty.exe 실행 -> 노트북 핫스팟 설정에서 라즈베리파이 IP 찾아서 PuTTY의 Host Name (or IP address) 에 넣기 -> Open -> 사용자 이름 입력 후 엔터 -> 사용자 비밀번호 입력 후 엔터 -> 원격 접속 완료
2. (Desktop environment)    
 여기선 XFCE desktop environment 사용. 설치하기.
```sudo apt update -> sudo apt install xfce4 xfce4-goodies -> (Select any display manager and press Enter.)```
3. VNC (remote버전) 설정    
    * 여기선 TigerVNC 씀.
    * sudo apt install tigervnc-standalone-server -> vncserver -> 패스워드 입력(6-8자) (나는 123456) -> 패스워드 재입력 -> view-only password 설정 여부(나는 n) -> 포트 5901 열림 (VNC 비번 바꾸고 싶으면 vncpasswd 입력)
    * vncserver -kill :1 -> ( 파일 ~/.vnc/xstartup 이 자동으로 생성되었으면 mv ~/.vnc/xstartup ~/.vnc/xstartup.bak ) -> nano ~/.vnc/xstartup (새로 생성) -> 우측 내용 복붙, 저장 후 나감. -> chmod +x ~/.vnc/xstartup 
    * -> 연결되는지 테스트하기 위해(secure connection 아님) vncserver -localhost no :1 -> 노트북에서 연결해봄 -> vncserver -kill :1 
    * 방법 1 : vncserver (5901 열음) -> 노트북 cmd 열음 -> ssh -L 59000:localhost:5901 -C -N -l hjrpb37 192.168.137.250 -> 노트북 vnc viewer에서 localhost:59000 연결 -> 연결완료
    * 방법 2 : vncserver (5901 열음) PuTTY 열음 -> 카테고리 Session 선택 -> Host Name -> 라즈베리파이 ip 넣음 -> 카테고리 SSH의 Tunnels 선택 -> Source port에 59000 입력, Destination에 localhost:5901 입력 -> Add 클릭 -> Open -> 로그인 -> vnc뷰어에서 localhost:59000 연결
4. VNC (remote버전) 연결    
    * VNC 첫 설정 이후 라즈베리파이 킬 때.
    * PuTTY 열음 -> 카테고리 Session 선택 -> Host Name -> 라즈베리파이 ip 넣음 -> 카테고리 SSH의 Tunnels 선택 -> Source port에 59000 입력, Destination에 localhost:5901 입력 -> Add 클릭 -> Open -> 아이디 비번 입력
    * -> vncserver (5901 열음) -> vnc viewer에서 localhost:59000 연결 -> continue -> vnc 비밀번호(123456) 입력 -> 완료.

### References
* [SSH connect in Windows CMD without PuTTY ](https://roboticsbackend.com/install-ubuntu-on-raspberry-pi-without-monitor/)
* [Download PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
* [라즈베리파이 화면을 노트북에서 보기](https://bytexd.com/how-to-install-configure-vnc-server-on-ubuntu/)
* [VNC의 두 가지(local, remote)(local이 원본)](https://www.reddit.com/r/linux4noobs/comments/b1qy53/can_i_remotely_use_ubuntu_without_a_monitor/)
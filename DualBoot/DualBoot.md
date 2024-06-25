# DualBoot
How to dualboot Windows and Ubuntu.

## Summary
Install Windows → Manage partitions in Windows → Install Ubuntu    
The reason to install Windows first: partition management is easier in Windows than in Ubuntu.

## Process
### Preparation
Create a Windows bootable USB and an Ubuntu bootable USB.
### Install Windows
1. Uncheck `Turn on fast startup`
   * 제어판 > 모든 제어판 항목 > 전원 옵션 > 시스템 설정 > 현재 사용할 수 없는 설정 변경 > 빠른 시작 켜기 체크해제
2. Connect the Windows bootable USB, boot the system, and access the BIOS by repeatedly pressing DEL, F2, or the appropriate key.
3. In the Boot menu, move the USB containing the OS to the top of the list. (You can use either the +/- keys or the ↑↓ keys.)
4. Save and exit BIOS.
5. After the system is rebooted, a window for installation of Windows appears.
6. Continue until setting partition.
   * “이 PC에서는 Windows 11을 실행할 수 없음” 오류:    
     레지스트리 편집창에서 키값 추가.    
     HKEY_LOCAL_MACHINE\SYSTEM\Setup\LabConfig BypassSecureBootCheck, BypassTPMCheck, BypassSecureRAMCheck, BypassSecureStorageCheck, BypassSecureCPUCheck.
7. 기존 데이터 유지하지 않는 옵션 설정하면 파티션 정해야 함. 파티션 다 지우고 새로 만들기로 원하는 용량 설정.
8. 윈도우 마저 설치
9. Uncheck `Turn on fast startup`
   * 제어판 > 모든 제어판 항목 > 전원 옵션 > 시스템 설정 > 현재 사용할 수 없는 설정 변경 > 빠른 시작 켜기 체크해제
10. 시작버튼 우클릭 > 디스크 관리 > 할당되지 않은 파티션 우클릭 > 새 단순 볼륨 > 볼륨 크기는 free space에 우분투 원하는 용량 남을정도 > 드라이브 문자 할당 아무거나 > 파일 시스템 NTFS, 단위크기 기본값, 빠른포맷 O > 마법사 마침.
### Install Ubuntu
1. 우분투18.04 USB 꽂은 후 데스크탑 키며 DEL 연타해서 BIOS 접속 (데스크탑은 GYGABYTE라서 DEL)
2. BIOS에서 OS가 들어있는 USB를 가장 위로 올림
3. BIOS 저장 후 나가기
4. 다시 켜지면 우분투 설치화면으로 감.
5. Try ubuntu 말고 install ubuntu 선택. 영어로 설치.
6. third-party 없이 설치
7. installation type은 something else 선택
8. free space 선택 후 + 클릭해서 Size는 원하는대로(free space 다 안 쓰면 남은 공간은 unusable 됨.) 그 밑은 Primary, Beginning of this space, Ext4 journaling file system, / 로 세팅하고 OK 누름
9. continue 누르고 install now 누름. 
10. 나머지 설정.
11. 설치 완료되면 restart 버튼 뜸. 누르고, usb빼라면 빼고 엔터누르면 됨.

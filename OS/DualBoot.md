# DualBoot
How to dualboot Windows11 and Ubuntu20.04


## Summary
Install Windows ➔ Manage partitions in Windows ➔ Install Ubuntu    
The reason to install Windows first: partition management is easier in Windows than in Ubuntu.


## Process
### Preparation
Create a Windows bootable USB and an Ubuntu bootable USB.

### Install Windows
1. Uncheck `Turn on fast startup`. (For BIOS)
   * 제어판 > 모든 제어판 항목 > 전원 옵션 > 시스템 설정 > 현재 사용할 수 없는 설정 변경 > 빠른 시작 켜기 체크해제
2. Connect the Windows bootable USB, boot the system, and access the BIOS by repeatedly pressing DEL, F2, or the appropriate key.
3. In the Boot menu, move the USB containing the OS to the top of the list. (You can use either the +/- keys or the ↑↓ keys.)
4. Save and exit BIOS.
5. After the system is rebooted, a window for installation of Windows appears.
6. Continue until setting partition.
   * “이 PC에서는 Windows 11을 실행할 수 없음” 오류:    
     레지스트리 편집창에서 키값 추가.    
     HKEY_LOCAL_MACHINE\SYSTEM\Setup\LabConfig BypassSecureBootCheck, BypassTPMCheck, BypassSecureRAMCheck, BypassSecureStorageCheck, BypassSecureCPUCheck.
7. If you choose the option to not preserve existing data, you must specify the partition.    
Delete all partitions and set the desired capacity for creating new ones.
8. Complete the installation of Windows.
9. Uncheck `Turn on fast startup`.
   * 제어판 > 모든 제어판 항목 > 전원 옵션 > 시스템 설정 > 현재 사용할 수 없는 설정 변경 > 빠른 시작 켜기 체크해제
10. Allocate partition for use in Windows.
      * 시작버튼 우클릭 > 디스크 관리 > 할당되지 않은 파티션 우클릭 > 새 단순 볼륨 > 볼륨 크기는 free space에 우분투 원하는 용량 남을정도 > 드라이브 문자 할당 아무거나 > 파일 시스템 NTFS, 단위크기 기본값, 빠른포맷 O > 마법사 마침.

### Install Ubuntu
1. Connect Ubuntu bootable USB, start the desktop, and press DEL (or the appropriate key) repeatedly to access BIOS.
2. In BIOS, move the USB containing the OS to the top.
3. Save and exit BIOS.
4. Upon restarting, it will boot into the Ubuntu installation screen.
5. Choose "Install Ubuntu" instead of "Try Ubuntu".
6. Choose English installation.
7. Install without third-party software.
8. Select "Something else" for installation type.
9. Choose `free space` and click `+`.    
   Set `Size` as maximum. Set them as `Primary`, `Beginning of this space`, `Ext4 journaling file system`, `/`, and click OK.
10. Press `Continue` and then `Install Now`.
11. Complete the remaining settings.
12. Once installation is complete, the `restart` button will appear. Press it.
13. After rebooting, when prompted, remove the USB and press Enter.
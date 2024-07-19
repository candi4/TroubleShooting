# Trouble_Ubuntu
Troubleshoot Ubuntu issues

## Ubuntu 20.04 screen freezing

**Reason**: Intel SoC computers using Linux encounter freezing due to compatibility issues with Intel processors' power-saving features.    
**Resolve**: It can be resolved by restricting low-power states of the processor.    
1. Open the grub file using the command `sudo gedit /etc/default/grub`.
2. Change `GRUB_CMDLINE_LINUX_DEFAULT="existing parameters"` to
3. `GRUB_CMDLINE_LINUX_DEFAULT="intel_idle.max_cstate=1"`.
4. Enter the command `update-grub`.
5. Reboot.     

Reference:    
[고통받던 ubuntu 20.04 화면 프리징 현상 해결](https://velog.io/@wltnrms0629/%EA%B3%A0%ED%86%B5%EB%B0%9B%EB%8D%98-ubuntu-20.04-%ED%99%94%EB%A9%B4-%ED%94%84%EB%A6%AC%EC%A7%95-%ED%98%84%EC%83%81-%ED%95%B4%EA%B2%B0)    
[intel_idle.max_cstate=1](https://medium.com/@dibyadas/intel-idle-max-cstate-1-b20281e4b2e2)    


# PyTorch
Issues of PyTorch


## Install (Ubuntu)
### Summary
(Optional) Install hangul    
➔ Install CUDA (automatically install GPU driver)    
➔ Install conda    
➔ Install PyTorch

### Install CUDA

w/ J.senior.    
1. After formating ubuntu, only installed hangul    
2. I want to use cuda11.7 because I used it on the other computers.    
Directly install cuda11.7. (Selected `deb (network)` because it is fastest among three choices.)     
3. Add in ~/.bashrc :
    ```
    export PATH="/usr/local/cuda-11.0/bin:$PATH"
    export LD_LIBRARY_PATH="/usr/local/cuda-11.0/lib64:$LD_LIBRARY_PATH"
    ```
4. Reboot    
5. Test using `nvcc`(CUDA) and `nvidia-smi`(GPU driver).    
6. After that, install conda and pytorch.    



#### Extra Tips

* Checking the GPU model and recommended driver
    ```
    ubuntu-drivers devices
    ```
* Installing driver.
    ```
    sudo apt install nvidia-driver-450
    ```

* Finding CUDA Toolkit compatible with your GPU in [this table](https://en.wikipedia.org/wiki/CUDA).    
    * e.g.    
    In the table `Compute Capability, GPU semiconductors and Nvidia GPU board products`,    
    `GP102` ➔ `6.1`.    
    In the table `Compute Capability (CUDA SDK support vs. Microarchitecture)`,    
    `6.1` -> `9.0 ~ 12.5`.
* Downloading CUDA Toolkit.    
    * e.g.    
    Operating System: Linux    
    Architecture: x86_64    
    Distribution: Ubuntu    
    Version: 20.04    
    Installer Type: deb (local)    


References:    
* [[CUDA] nvcc가 안될 때 ~/.bashrc 수정](https://yoonchang.tistory.com/27)    
* [Ubuntu 장착된 CPU 및 GPU 그래픽카드 확인 코드](https://nuggy875.tistory.com/30#google_vignette)    
* [CUDA Toolkit and Corresponding Driver Versions](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html#id4)    
* [CUDA toolkit 설치 완벽 정리](https://velog.io/@jk01019/CUDA-toolkit-%EC%84%A4%EC%B9%98-%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC)    
* [[Ubuntu 20.04 LTS]Nvidia드라이버 설치하기](https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)    

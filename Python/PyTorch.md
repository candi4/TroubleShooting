# PyTorch
Issues of PyTorch


## Install (Ubuntu)

### Install CUDA
1. Check the GPU model on Ubuntu.
    ```
    lspci | grep -i VGA
    ```
    e.g. `GP102`

2. Find CUDA Toolkit compatible with your GPU in [the table](https://en.wikipedia.org/wiki/CUDA).    
e.g.    
In the table `Compute Capability, GPU semiconductors and Nvidia GPU board products`,    
 `GP102` ➔ `6.1`.    
 In the table `Compute Capability (CUDA SDK support vs. Microarchitecture)`,    
 `6.1` -> `9.0 ~ 12.5`
3. Download CUDA Toolkit.    
    * e.g.    
    Operating System: Linux    
    Architecture: x86_64    
    Distribution: Ubuntu    
    Version: 20.04    
    Installer Type: deb (local)    


Reference:    
[Ubuntu 장착된 CPU 및 GPU 그래픽카드 확인 코드](https://nuggy875.tistory.com/30#google_vignette)    
[Table `CUDA Toolkit and Corresponding Driver Versions`](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html#id4)    

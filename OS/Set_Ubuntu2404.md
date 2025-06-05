# Ubuntu 24.04 setup
## Repository change
### [24.04]
  ```
  sudo gedit /etc/apt/sources.list.d/ubuntu.sources
  ```
- URIs change(both of deb types)
	URIs: http://kr.archive.ubuntu.com/ubuntu/ -> http://mirror.kakao.com/ubuntu/
### [22.04]
```
sudo gedit /etc/apt/sources.list
```
kr.archive.ubuntu -> mirror.kakao    
(not security)

## install Hangul
- Settings -> system -> region & language
- Manage installed languages -> install/remove languages -> 'Korean' check -> reboot
- open terminal -> ibus-setup -> input method -> add -> 'Hangul'
- Settings -> keyboard -> Input sources add 'Korean(Hangul)' -> remove others -> preference of Korean(Hangul) -> Hangul Toggle key 'add'

## Vscode
- Install vscode
- Extension
	- python, python Extension pack, Black formatter
	- C++, C++ extension pack. Clang-format
	- Remote - SSH
	- indent rainbow
	- Markdown all in one / markdown pdf
- Setting
	- File -> preference -> settings
		- zoom level
		- font size

## Conda install
- install conda :https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html

## CUDA install
- install cuda : https://developer.nvidia.com/cuda-12-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=24.04&target_type=deb_local
- post-installation
  ```
	export PATH=${PATH}:/usr/local/cuda/bin
	export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda/lib64
  ```

## LAN driver
- check model
  ```
  lspci | grep -i ethernet
  ```
- download driver : https://www.realtek.com/Download/List?cate_id=584
- unzip and install
  ```
  sudo ./autorun.sh
  ```

## bashrc alias
```
alias eb='gedit ~/.bashrc'
alias sb='source ~/.bashrc'
alias cac='conda activate'
alias cde='conda deactivate'
# ==== Show Local Installed CUDA and cuDNN Versions (JSON + Header Parse) ====

# Check CUDA version from version.json
if [ -f /usr/local/cuda/version.json ]; then
    cuda_version=$(grep -A 2 '"cuda"' /usr/local/cuda/version.json | grep '"version"' | head -n 1 | awk -F '"' '{print $4}')
    echo "CUDA version : ${cuda_version}"
else
    echo "CUDA version : not found"
fi

# Check cuDNN version from cudnn_version.h
if [ -f /usr/include/x86_64-linux-gnu/cudnn_version.h ]; then
    cudnn_major=$(grep "#define CUDNN_MAJOR" /usr/include/x86_64-linux-gnu/cudnn_version.h | awk '{print $3}')
    cudnn_minor=$(grep "#define CUDNN_MINOR" /usr/include/x86_64-linux-gnu/cudnn_version.h | awk '{print $3}')
    cudnn_patch=$(grep "#define CUDNN_PATCHLEVEL" /usr/include/x86_64-linux-gnu/cudnn_version.h | awk '{print $3}')
    echo "cuDNN version : ${cudnn_major}.${cudnn_minor}.${cudnn_patch}"
else
    echo "cuDNN version : not found"
fi

# ==== End CUDA/cuDNN Version Check ====
```

## GPU driver
For NVIDIA GeForce RTX 5090
```
sudo apt remove --purge nvidia*
sudo apt autoremove
sudo apt install nvidia-driver-570-open
```

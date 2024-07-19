# conda
Issues with conda

## install (Ubuntu)
1. Download Anaconda Individual Edition in [the Anaconda official website](https://www.anaconda.com/download/success).
    ```
    wget https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
    ```
2. Navigate to the folder where Anaconda was downloaded.
3. (Optional) Verify the data integrity using the sha256sum command.
    ```
    sha256sum Anaconda3-2020.11-Linux-x86_64.sh
    ```
    In the results window, copy the hash value and check if it matches the hash value shown on [Anaconda hash page](https://docs.anaconda.com/anaconda/hashes/).
4. Run the Anaconda installation script to begin the installation.
    ```
    bash Anaconda3-2020.11-Linux-x86_64.sh
    ```
    You can set a preferred directory.   
    Enter yes for this: `Do you wish to update your shell profile to automatically initialize conda?`
5. Add a line into `bashrc` to use anaconda prompt.
    ```
    gedit ~/.bashrc
    ```
    Add a line: `export PATH=~/anaconda3/bin:~/anaconda3/condabin:$PATH`
    ```
    source ~/.bashrc
    ```
6. check if the conda installation was successful.
    ```
    conda -V
    ```
7. (Optional) To prevent the terminal from defaulting to the Anaconda prompt upon launch:
    ```
    conda config --set auto_activate_base False
    ```
    Use `conda activate` and `conda deactivate` to launch and deactivate anaconda prompt in the future.

Reference: [[우분투/Ubuntu 20.04] 우분투에 아나콘다 설치 / Install Anaconda on Ubuntu](https://ieworld.tistory.com/12)    


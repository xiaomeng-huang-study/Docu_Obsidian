# Tutorial for installing Cuda for Acceleration in WSL2 

## NVIDIA CUDA Driver on Windows 
- visit [official website](https://www.nvidia.com/Download/index.aspx?lang=en-us ) , download the version for windows and install 

## Get the NVIDIA Public Key 
```bash
sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub 
```
### Trouble shooting 
```bash
GPG error: http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
```
- add the public key 
```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC
```

## Add NVIDIA to the Source List Directory 
```bash
sudo sh -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list'
```
```bash
sudo apt-get update
```

## Install CUDA Toolkit on WSL 
- visit [official website](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#cuda-support-for-wsl-2) and use the recommended option 1 

## Test 
### Nvidia Cuda Driver 
```bash
nvidia-smi
```
### CUDA Toolkit 
```bash
nvcc --version
```
#### Trouble shooting 
- `nvcc command not found` 
	- in `~/.bashrc` 
		```bash
		export PATH="/usr/local/cuda-12.3/bin:$PATH"
		export LD_LIBRARY_PATH="/usr/local/cuda-12.3/lib64:$LD_LIBRARY_PATH"
		```
		(replace `cuda-12.3` with actual version) 

## Install the CUDA and cuDDN Libraries 
```bash
sudo apt-get install --yes --no-install-recommends cuda-12-3 libcudnn8 libcudnn8-dev
```
- add to `~/.bashrc` 
	- find the path 
		```bash
		whereis libcudnn.so
		whereis cudnn.h
		```
	- copy the path 
		```bash
		export CUDNN_LIBRARY="/usr/lib/x86_64-linux-gnu/libcudnn.so"
		```
		```bash
		export CUDNN_INCLUDE_DIR="/usr/include/cudnn.h"
		```

## Test for CUDA in WSL2 
follow the tutorial on https://ubuntu.com/tutorials/enabling-gpu-acceleration-on-ubuntu-on-wsl2-with-the-nvidia-cuda-platform#4-compile-a-sample-application 
# Tensorflow gpu 2.0 intallation with anaconda on ubuntu 18.04

Since Nov 1st anaconda fully supports the gpu version tensorflow, the installation of tensorflow 2 with GPU became much traightforward. This guide can give step-by-step guide to help one get your machine set up. You may have to have a nvidia graphics card which support the cuda calculation. The script to check the availability of your GPU is to type in terminal (ctrl+alt+T):

```shell_session
$ lspci | grep -i nvidia
```

### Step 1. Clean previous gpu drivers and install latest nVidia Drivers):
  - Open terminal and enter :
    ```shell_session
    $ sudo add-apt-repository ppa:graphics-drivers/ppa
    $ sudo apt-get update
    $ sudo apt-get purge nvidia*
    ```
   - Then reboot
   ```shell_session
   $ sudo reboot
   ```
    
  - Install a proper driver and reboot
    ```shell_session
    $ sudo apt update
    $ sudo ubuntu-drivers autoinstall
    $ sudo reboot
    ```
  - To check the installed drivers, you may type the command which is:
    ```shell_session
    $ nvidia-smi
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 440.26       Driver Version: 440.26       CUDA Version: 10.2     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce GTX 108...  Off  | 00000000:01:00.0 Off |                  N/A |
    |  0%   26C    P8    13W / 280W |  10788MiB / 11178MiB |      5%      Default |
    +-------------------------------+----------------------+----------------------+
                                                                              
    ```
    The import info include the Drive version and Cuda version. Don't worry about the cuda version. For my server it's 10.2. But by creating a virtual environment with anaconda, we can have 10.0 version inside of the new environment. 
    You may also find some interesting figures which track the usage of GPU. It needs to be noted that the refresh frequency of this table is compariably slow. Tracking the performance during very short period can be very hard as they may be not observed.
    
## Step 2. Set up TensorFlow 2.0 in Anaconda
  Anaconda as a complete package management tool can easily install many package without worrying about the compatibility. It's because TensorFlow needs CUDA and cuDNN but the latest version of CUDA or cuDNN may not support the current version of TensorFlow. For example the CUDA 10.1 and 10.2 does not support Tensorflow 2.0. The comaptibility issue can make GPU not detected by TensorFlow.
  
  Installing TensorFlow by Anaconda is very clear. The first step is to make sure your anaonda is the latest version.
  
  - Update Anaconda to date
    ```shell_session
    $ conda update conda
    $ conda update conda-build 
    ```
   Updating the conda-build is the key point that can directly influence the version of packages forged from Anaconda Cloud. It gives the newest package compatibility otherwise you may have the chance to install TensorFlow 1.14 or lower.

  - Create a new environment
  
    ```shell_session
    $ conda create -n your_envs_name python=3.7
    ```
  - If successful, check the current environment. It will lit all available environments in anaconda
  
    ```shell_session
    $ conda info --envs
    ```
   
  - Activate the newly built environment and install TensorFlow gpu. Check the TensorFlow version which should be 2.0 and the CudaToolKit should have version 10.0. 
  
    ```shell_session
    $ conda activate your_envs_name
    $ conda install tenorflow-gpu
    ```
  - After installation, you can check the already installed packages by using:
    ```shell_session
    $ conda list
    ```
 
 ### Step 3. Verifying the installation
  - Run the following code to verify the installation
    ```shell_session
    $ python3
    >>> import tensorflow as tf
    >>> tf.test.is_gpu_available(
    cuda_only=False,
    min_cuda_compute_capability=None)
    ```
  
  It will return True if a GPU device of the requested kind is available.
  
 ### Step 4. Some often used packages 
  The listed packages are what we normally used in my research. Most of them are popular for all python users. I don't give the description as it's easy to google them. Do not install them in the base envs. You have to activate the target virtual environment and run the command within the activated envs. It helps once your envs is broken, you can easily remove all envs without re-install the anaconda itself.
  
    $ conda activate your_envs_name  #activate your envs first!
    
    $ conda install pandas
    $ conda install scikit-learn
    $ conda install numba
    $ conda install matplotlib
    $ conda install statsmodels
    $ conda install xlrd
    $ pip install memory_profiler
  
  


# PhD-Finance-Machine-learning

# Introduction
This project tries to include almost all necessary knowledge about doing a PhD in Finance using Machine learning. 

As machine learning rapidly merged with traditional social science, it's very attractive to apply Machine learning to finance field, especially prediction related problem.

Currently, it includes:
  1. The machine learning algorithm and intuitive applications
  1. Related mathematics algorithm. 
  1. Trading strategies
      1. Momentum Strategies
      1. Pair Trading Strategies
  1. Asset pricing 
      1. Retrieve data from WRDS
      1. Common risk factors and firm characteristics
 
# About me
 
Third-year PhD. candidate in finance at Durham University.
 
5 years of data analysing and 2-year quant experience specializing in machine learning and equity prediction.Interested in fancy technologies and equipment. Familiar with many kinds of derivatives, stocks and bonds, and devoted to more accurate asset pricing and forecasting methods. 
 
A cat lover and a good chef (Chinese Cuisine and Sichuan hotpot). If you find me, I would very like to trest you a special dinner with my personal menue.


# How to find related reference

Each research field has a trend. Traditional research area can directly search the published resources such as the web of science  (www.webofknowledge.com) to create the personal library. While for some newly established intersection research such as machine learning in finance filed,  papers tend to be in different areas. Publishing papers require a long time. Researchers would be more willing to published their working paper in some public database such as SSRN and arXiv before it's too late. 

Normally the machine learning in fiance papers can be mostly (not all) found in the following places:

1. Working papers in public database: SSRN(more finance and social science papers), arXiv(more computer science paper) and some university-owned database(MIT, Chicago booth)

2. Journal paper:
    1. Expert System with Applications (3)
    1. Management Science (4*)
    1. Journal of Financial Economics (4*)
    1. Journal of Emperical Finance (3)
    

As papers are not published in the same journal, I would highly recommend using google scholar as the main reference management website. Of course, you may use the EndNote (if your university offers the free student version), Melody(Free) or other software. But google scholar for me is good enough to support every function required. 

Some functions are extremely useful in google scholar after you sign in your google account.
1. 'Labels': A tag-like button just below the search box. You may category your papers with this tool. Can help you manage the big amount of literature.
1. 'Related Articles': A button under the title of the paper. It may automatically research all related articles to this topic. The result may include all possible working papers, conference papers and journal papers from many fields in the most popular order. It can make one quickly grasp the recent trend and result of one topic.
1. 'Cite': A double-quotation-mark-like button. Generate multiple format citations for Bibtex, EndNote, et al. One can export multiple citations for selected papers by using the 'Export' button below the search box. As I don't use EndNote, the Bibtex format is the most used. 
1. 'Anytime': Some years listed in the left-hand side. We would have more cared about the recently 2 years papers or sometimes the latest published paper. This function filters papers by years. Normally papers within 5 years are comparably new and some working papers within one year are great to learn the hot topics and the most popular issues.



# Choose a editor to write

The most frequently used editor in normal life would be the Word from Microsoft Office. While it's not the best choice for acadimic writing. For my point of view, the only one option for researchers is LaTex which offered the high quality formatting system and makes your papers more professional. You may write your CV, cover letter and even apologies letter to make them proper and formal. The advantage of LaTex is:
1. Easy to manage Bibliography using bib file. The bib file can reuse in the next paper
1. Once get on the board, you will forget about the fear from adjusting the linewith and font style. 
1. Abundant of templates and easy to use with one mouse click.

There are plenty of LaTex editors and what I use is OverLeaf which is a web broswer based online editor. Since all data are uploaded and saved on the cloud. As long as you can find a computer with Wifi, you can start to work. Almost all necessary packages are installed already and you will never worried about the computer crash as it will automaticlaly save the documents from time to time. 


# Tensorflow gpu 2.0 intallation with anaconda on ubuntu 18.04

Since Oct 1st anaconda fully supports the gpu version tensorflow, the installation of tensorflow 2 with GPU became much traightforward. This guide can give step-by-step guide to help one get your machine set up. You may have to have a nvidia graphics card which support the cuda calculation. The script to check the availability of your GPU is to type:

```shell_session
$ lspci | grep -i nvidia
```

### Step 1 Clean previous gpu drivers and install latest nVidia Drivers):
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
    You may also find some interesting numbers that can help you track the usage of GPU. Need to be noted that the fresh frequency of this chat is compariably slow. Tracking some very short period peak time may be not observed.
    
## Set up TensorFlow 2.0 in Anaconda
  Anaconda as a complete package management tool can easily help us install many package without worrying about the compatibility
  
  - We are using version 10.0 since it is the working CUDA driver with Tensorflow 2.0 without any bugs. You may upgrade in the future but for now, let's stick with it.
  
### Step 1 (Installation):
  - Go to nVidia cuda archive https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork and download the installer type: Network
  - link to the installer : https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
  - Then use the following commands inside the folder where you have downloaded the installer,
  ```shell_session
  $ sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
  $ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
  $ sudo apt-get update
  $ sudo apt-get install cuda-10-0
  ```
  - NOTE: Make sure you use "sudo apt-get install cuda-10-0" incase if you have used "sudo apt-get install cuda" , it will insatll cuda-10.1
 
### Step 2 (Adding PATH):
  - After the installation we have to set the path for the Graphics card to locate the CUDA libraries. open,
  ```shell_session
  $ sudo nano ~/.bashrc
  ```
  - Enter the following and save the bashrc to set the PATH variables.
  ```shell_session
  export PATH=/usr/local/cuda-10.0/bin${PATH:+:$PATH}}
  export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
  ```

## Installing cuDNN

  - Download the cuDNN from https://developer.nvidia.com/rdp/cudnn-archive
  - You should have a membership account to download the cuDNN libraries.
  - After logging in download cuDNN v7.6.0 for CUDA 10.0, Get the Linux tar package.
    https://developer.nvidia.com/compute/machine-learning/cudnn/secure/7.6.4.38/Production/10.0_20190923/cudnn-10.0-linux-x64-v7.6.4.38.tgz
  - Go to the folder where the archive got downloaded, in the terminal,
  ```shell_session
  $ tar -xzvf cudnn-10.0-linux-x64-v7.6.4.38.tgz
  ```
  - Then type the following to move the libraries to the appropriate folders,
  ```shell_session
  $ sudo cp cuda/include/cudnn.h /usr/local/cuda/include
  $ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
  $ sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
  ```

## Installing pip3 and Tensorflow-2.0-GPU

  - The support for python v2.7 end official from 2020, So it's better if we can stick with python version 3.6

### Step 1 (Installing pip3):
  - Use the following commend to install pip3 in your PC,
  ```shell_session
  $ sudo apt-get install python3-pip
  $ sudo pip3 --upgrade pip
  ```
  
### Step 2 (Installing Tensorflow):
  - Now let's install Tensorflow 2.0
  ```shell_session
  $ pip3 install tensorflow-gpu==2.0.0
  ```
### Step 3 (Verifying the installation):
  - Run the following inside python3 terminal to verify the installation
  ```shell_session
  $ python3
  >>> import tensorflow as tf
  >>> hello = tf.constant('hello tensorflow')
  >>> x = [[2.]]
  >>> print('hello, {}'.format(tf.matmul(x, x)))
  2019-00-00 16:04:38.589080: I tensorflow/stream_executor/platform/default/dso_loader.cc:42] Successfully opened dynamic library   libcublas.so.10.0
  hello, [[4.]]
  >>> exit()
  ```
### That's it you have successfully Tensorflow-2.0-GPU with CUDA 10.0.
  


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
    You may also find some interesting numbers that can help you track the usage of GPU. Need to be noted that the fresh frequency of this chat is compariably slow. Tracking some very short period peak time may be not observed.
    
## Step 2. Set up TensorFlow 2.0 in Anaconda
  Anaconda as a complete package management tool can easily help us install many package without worrying about the compatibility. It's because TensorFlow needs CUDA and cuDNN but the latest version of CUDA or cuDNN may not support the current version of TensorFlow. For example the CUDA 10.1 and 10.2 does not support Tensorflow 2.0. It will make GPU not detected when running codes. 
  
  Installing by Anaconda is just so simple. The steps are:
  - Update Anaconda to date
    ```shell_session
    $ conda update conda
    $ conda update conda-build 
    ```
   It's necessary to update conda-build. It can give the newest package compatibility otherwise you may have the chance to install TensorFlow 1.14 or lower.

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
  The listed packages are what we normally used in both research and industry. I don't give the description as it's easy to google online. Do not install them in the base envs. You have to activate the target virtual environment and run the command within the activated envs. 
  
    ```shell_session
    $ conda activate your_envs_name  /activate your envs first!
    $ conda install pandas
    $ conda install scikit-learn
    $ conda install numba
    $ conda install matplotlib
    $ conda install statsmodels
    $ conda install xlrd
    $ pip install memory_profiler
    ```
  
  


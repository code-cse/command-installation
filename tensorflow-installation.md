
##  [Installation command](command-installation) 
This repository contains the command for different package installation.

### Tensorflow-GPU Installation

![alt text](images/tf.jpg)

[image-source][https://www.tensorflow.org/]

##### Install Nvidia-Driver for GPU (for tensorflow <= 1.13)

It was updating the GPU driver to the latest and installing the cuda toolkit. First, the ppa was added and GPU driver installed:


`sudo add-apt-repository ppa:graphics-drivers/ppa`

`sudo apt update`

`sudo apt install nvidia-390`

After adding the ppa, it showed options for driver versions, and 390 was the latest 'stable' version that was shown.

Then install the cuda toolkit

`sudo apt install nvidia-cuda-toolkit`

Then reboot

`sudo reboot`


##### Install tensorflow

##### Create virtual-env

`pip install virtualenv`

`virtualenv --python==python3 env_name`

`e.g.`  `virtualenv --python==python3 gpu_env`

`source gpu_env/bin/activate`


For python3 

`pip3 install tensorflow-gpu==version`

`e.g.`  `pip3 install tensorflow-gpu==1.12`

For python2

`pip2 install tensorflow-gpu==version`

`e.g.`  `pip2 install tensorflow-gpu==1.12`



### Tensorflow-CPU Installation

![alt text](images/tf.jpg)

[image-source][https://www.tensorflow.org/]

##### Create virtual-env

`pip install virtualenv`

`virtualenv --python==python3 env_name`

`e.g.`  `virtualenv --python==python3 cpu_env`

`source cpu_env/bin/activate`


For python3 

`pip3 install tensorflow==version`

`e.g.`  `pip3 install tensorflow==1.12`

or

for latest version

`e.g.`  `pip3 install tensorflow` 


For python2

`pip2 install tensorflow==version`

`e.g.`  `pip2 install tensorflow==1.12`

or

for latest version

`e.g.`  `pip2 install tensorflow` 






## Another Option

his is taken from the Google instructions, but with the proper versions of CUDA that will work for TensorFlow v1.7:

curl -O https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb

sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb

sudo apt-get update

sudo apt-get install cuda-9-0

sudo nvidia-smi -pm 1


Then you should verify that everything is installed and working with:


nvidia-smi


Google’s instructions do not mention installing the cudnn, but it appears to be required. To download it you need to register with Nvidia’s Developer’s Program, download it and then upload it to your instance. I uploaded it using SCP which took a while. The file I used was libcudnn7_7.0.4.31–1+cuda9.0_amd64.deb, which is the version required for cuda-9.0 with TensorFlow 1.7. Once it is uploaded you can install it with:


sudo dpkg -i libcudnn7_7.0.4.31-1+cuda9.0_amd64.deb


Once this is all installed you need to set some PATH variables. Google’s instructions add the variable to the path temporarily, so need to be run every time you boot the instance. This will add them permanently:

echo 'export CUDA_HOME=/usr/local/cuda' >> ~/.bashrc

echo 'export PATH=$PATH:$CUDA_HOME/bin' >> ~/.bashrc

echo 'export LD_LIBRARY_PATH=/usr/local/cuda/extras/CUPTI/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc

source ~/.bashrc


Finally you can install TensorFlow:


sudo apt-get install python3-dev python3-pip libcupti-dev

sudo pip3 install tensorflow-gpu

Finally, Google suggests a couple of settings to optimize the GPU performance:

### this applies to all GPUs


sudo nvidia-smi -pm 1


### these only apply to Nvidia Tesla K80s


sudo nvidia-smi -ac 2505,875

sudo nvidia-smi --auto-boost-default=DISABLED


### Cleaning the nvidia driver:
* After Cleaning cache, you can try these,

* dpkg -l | grep cuda- | awk '{print $2}' | xargs -n1 sudo dpkg --purge

* df -h

* sudo apt-get purge nvidia*

* sudo apt-get -f install

* sudo apt autoremove

* Hope, this might help you. Cheers


##  [Installation command](command-installation) 
This repository contains the command for different package installation.

### Tensorflow-GPU Installation

![alt text](images/tf.jpg)

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

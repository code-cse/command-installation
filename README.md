
##  Installation command 
This repository contains the command for different package installation.

### Tensorflow-GPU Installation

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

For python3 

`pip3 install tensorflow-gpu==version`

`e.g.`  `pip3 install tensorflow-gpu==1.12`

For python2

`pip2 install tensorflow-gpu==version`

`e.g.`  `pip2 install tensorflow-gpu==1.12`

# AutoMani
A deep learning model to perfrom segmetation on images provided a robot and provide contours of finger. This is model provided information of all position all the pixels related to finger.The presentation slides for this project are provided as [Google Slides](https://drive.google.com/open?id=1fJP-UhYJfN1BGsrhc85v0OSsd_AJIWoYlNtNQ7Ev6mU)

## Problem Statement
I worked on this project to help a company that is automating manicure process. They have trouble to guide the robot during manicure process with traditional methods like canny edge detection which fails to provide contours of finger during painting process. So I want to introduce a deep learning solution to track down micro movements of finger that can guide robot.

## Requisites

- Ubuntu 16.04 LTS
- Python 3
- NVIDIA GPU (compute capability 6.0+) & CUDA cuDNN
- TensorFlow 1.14

## Build Environment
- Create a new anaconda environmnet to avoid confilts with other working environments. Run the following command to install all the required files. 
```  
pip install -r requiremnts
```  
## Setup
This project comes in two repositories. This repository, for general purpose scripts and documentation, and a forked version of the [TensorFlow model](https://github.com/Naveen-Dodda/models) repository which is modified to support finger segmentation application. 
Clone this repo to a machine with an NVidia card (tested on aws p2.xlarge instance).

- Clone this repository to your home folder:
```
cd ~
git clone https://github.com/Naveen-Dodda/insight-auto-mani.git
cd insight-auto-mani.git
```  

- Clone the forked version of the [TensorFlow model](https://github.com/Naveen-Dodda/models) repository which has been modified for this project. Once you have cloned this repository, change your present working directory to models/reserarch/ and add it to your python path. If you want to add it permanently then you will have to make the change in your .bashrc file or you could add it temporarily for current session using the following commands:

```
cd ~
git clone https://github.com/Naveen-Dodda/models.git
cd models/research
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
protoc object_detection/protos/*.proto --python_out=.

``` 


## Run Inference

- A Frozen graph is provided in the repo to run your test right away. open the interactive jupyter notebook  models/reserach/Evalution_of_Auto_Mani.ipynb in the Tensorflow models repository. Please adjust the path in the notebook and point it to right directory of test images in the repo. 


## Build and Train a Coustom Model
- All the instructions to build and train the model on a new data set is given  in Build and Train folder. 



## Reslusts 
- The current model used for segmetation task is Mask_RCNN with inception v2 as back bone network, trained on 130 images on single gpu, can performe segmetation task with pixel to pixel accoracy of 95.83%. 
- Inference speed of model is 4fps on single gpu.
- Intersection Over Union (IOU) = 0.953
- Pixel Accuracy= 97.34

- 

# Setting up TF Records
Make sure that data set is stored in this specific format'
'
'
'
'
'
'

TensorFlow API accepts data in tf record format, so in order to facilitate training process on a new data set we have to generate a new tf record file. I have upadted tf_record.py to create a tf record for Coral Labs data set. Name of the modeified file is in this folder as Manicure_mask_rcnn_tf_record.py. You need to take this script and place it in the models/research/object_detection/dataset_tools.

_Note: create_mask_rcnn_tf_record.py is modified in such a way that given a mask image, it should found bounding box around objects on it owns and hence you don't need to spend extra time annotating bounding boxes but it comes at a cost, if mask image has multiple objects of same class then it will not be able to find bounding box for each object of the same class rather it will take a bounding box encompassing all objects of that class.

If you have multiple objects of the same class in some images then use labelImg library to generate xml files with bounding boxes and then place all the xml file generated from labelImg under Annotations/xmls folder. once you have bounding box annotation in xml files use create_mask_rcnn_tf_record_multi.py to convert the data to tensorflow record format.

To download labelImg library along with its dependencies go to THIS LINK. Once you have the labelImg library downloaded on your PC, run lableImg.py. Select JPEGImages directory by clicking on Open Dir and change the save directory to Annotations/xmls by clicking on Change Save Dir. Now all you need to do is to draw rectangles around the object you are planning to detect. You will need to click on Create RectBox and then you will get the cursor to label the objects. After drawing rectangles around objects, give the name for the label and save it so that Annotations will get saved as the .xml file in Annotations/xmls folder._r




## Problem Statement
I worked on this project to help a company that is trying to automate manicure process. They have trouble to guide the robot during manicure process ; traditional methods like canny edge detection fails to provide contours of finger during painting process. So I want to introduce a deep learning solution to track down micro movements of finger that can guide robot.

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

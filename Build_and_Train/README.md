## Setting up TF Records
- Make sure that data set is stored in this format, to make it convienet for creating tf record and training. Store all the raw images in .jpg format in a folder and all ground truth in .png format images other folder. Ensure names of raw image and corresponding ground truth are same. As a refrence you can how i have saved test images. Now lets move on to creating a tf_record.

- TensorFlow API accepts data in tf record format, so in order to facilitate training process on a new data set we have to generate a new tf record file. I have upadted tf_record.py to create a tf record for Coral Labs data set. Name of the modeified file is in this folder as Manicure_mask_rcnn_tf_record.py. You need to take this script and place it in the models/research/object_detection/dataset_tools.Naming conventions of classes are stored in lable.pbtxt. Now in the command interface run the following commands.

```
cd models/research

python object_detection/dataset_tools/create_mask_rcnn_tf_record.py --data_dir=<path_to_your_dataset_directory> --annotations_dir=<name_of_ground_truth_images_directory> --image_dir=<name_of_Raw_images_directory> --output_dir=<path_where_you_want_record_file_to_be_saved> --label_map_path=<path_of_label_map_file>
```  

## Training

- First important step is choosing the right model. I prefered to start my training over a pre-trained model from [TensroFlow Zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md). each model comes with a config file but i highly recommend to use the config files from [here] (https://github.com/tensorflow/models/tree/master/research/object_detection/samples/configs); which are upto date. You can aslo check the config file in this repo which is modified for this porject. Make changes in the config file to start training. 

```
python object_detection/legacy/train.py --train_dir=<path_to_the folder_for_saving_checkpoints> --pipeline_config_path=<path_to_config_file>

```

## Building a model to do inference. 

- After training, in order to do inference task, forzen graph must be generated from saved check_points. Execute following commands to build a inference graph. Now you can follow inference procedure in main readme to test new model.

```
python object_detection/export_inference_graph.py --input_type=image_tensor --pipeline_config_path=<path_to_config_file> --trained_checkpoint_prefix=<path to saved checkpoint> --output_directory=<path_to_the_folder_for_saving_inference_graph>
```

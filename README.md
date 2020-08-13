# Drone-Detection
Detect drones from input image, video or real-time feed.

## Requirements

- Refer to requirement.txt for environment specifications.
- Download the pre-trained YOLOv3 weights from [here.](https://pjreddie.com/media/files/yolov3.weights)
- Download an image of a dog to test object detection.

  > `$ python yolo3_one_file_to_detect_them_all.py -w yolo3.weights -i dog.jpg`

- Download pretrained weights for backend from [here.](https://1drv.ms/u/s!ApLdDEW3ut5fgQXa7GzSlG-mdza6) This weight must be put in the root folder of the repository. 

## Dataset
YOLOv3 training requires images with .xml files in PASCAL-VOC format.

Click [here] to Download Drone Dataset with .xml files in PASCAL-VOC format.

Alternatively, if you want to create your own dataset, follow these steps:
   1. Collect images from Kaggle Dataset or Google Images.
   2. Download LabelImg(a graphical image annotation tool) from [this GitHub Repo.](https://github.com/tzutalin/labelImg)
   3. Setup LabelImg and draw a box around the object of interest in each image using the tool to generate XML files.

## Training

### 1. Edit config.json

```sh
{
    "model" : {
        "min_input_size":       288,
        "max_input_size":       448,
        "anchors":              [17,18, 28,24, 36,34, 42,44, 56,51, 72,66, 90,95, 92,154, 139,281],
        "labels":               ["drone"]
    },

    "train": {
        "train_image_folder":   "F:/Drone/Drone_mira_dataset/images/",
        "train_annot_folder":   "F:/Drone/Drone_mira_dataset/annots/",
        "cache_name":           "drone_train.pkl",

        "train_times":          8,       # the number of time to cycle through the training set, useful for small datasets
        "pretrained_weights":   "",      # specify the path of the pretrained weights, but it's fine to start from scratch       
        "batch_size":           2,       # the number of images to read in each batch
        "learning_rate":        1e-4,    # the base learning rate of the default Adam rate scheduler
        "nb_epochs":            50,      # number of epoches
        "warmup_epochs":        3,       
        "ignore_thresh":        0.5,
        "gpus":                 "0,1",

        "grid_scales":          [1,1,1],
        "obj_scale":            5,
        "noobj_scale":          1,
        "xywh_scale":           1,
        "class_scale":          1,

        "tensorboard_dir":      "logs",
        "saved_weights_name":   "drone.h5",
        "debug":                true    # turn on/off the line that prints current confidence, position, size, class losses and recall
    },

    "valid": {
        "valid_image_folder":   "C:/drone/valid_image_folder/",
        "valid_annot_folder":   "C:/drone/valid_annot_folder/",
        "cache_name":           "drone_valid.pkl",

        "valid_times":          1
    }
}

```


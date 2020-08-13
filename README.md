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
   >1. Collect images from Kaggle Dataset or Google Images.
   >2. Download LabelImg(a graphical image annotation tool) from [this GitHub Repo.](https://github.com/tzutalin/labelImg)
   >3. Setup LabelImg and draw a box around the object of interest in each image using the tool to generate XML files.
                  


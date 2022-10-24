# License Plate Detection based on Yolov7 and OCR systems: PyTesseract, EasyOCR, Attention OCR (soon)


## Installation

``` shell
# apt install required packages
sudo apt update
sudo apt install -y zip htop screen libgl1-mesa-glx tesseract-ocr pipenv
  
# clone repo:
git clone https://github.com/NabatchikovIlya/license-plate-detection.git

# create virtualenv:  
pipenv install

# activate virtualenv:  
pipenv shell

# download data:  
gdown -O data/ 'https://drive.google.com/uc?id=1nps9Cv4-kqPZAA92sDP7rnAX76ABgdhy'

# download weights:  
gdown -O data/ 'https://drive.google.com/uc?id=1HH7ei39rPZNxYqH4TTQom01UFlYvxS04'

```

## Inference
On video:
``` shell
pipenv run python detect.py --weights data/yolov7_plate_number.pt --conf 0.25 --img-size 640 --source yourvideo.mp4
```

On image:
``` shell
pipenv run python detect.py --weights data/yolov7_plate_number.pt --conf 0.25 --img-size 640 --source inference/images/test_range.jpg
```

## About data

RoboFlow: [link1](https://universe.roboflow.com/public-workspace-n6wxn/license-plate-detection-g0oub), [link2](https://universe.roboflow.com/public-workspace-n6wxn/license-plate-nightdetect/dataset/1), [link3](https://universe.roboflow.com/augmented-startups/vehicle-registration-plates-trudk/browse?queryText=&pageSize=50&startingIndex=0&browseQuery=true)


## Architecture

Object detector + OCR system. \
As a detector we used: YOLOv5 and YOLOv7 \
As an OCR system we used: PyTesseract and EasyOCR

## Example
<p align="center"><img src="./inference/images/example.png" alt="detection" width="70%"></p>


## Experiments setup

- Hardware
    - CPU count: 1
    - GPU count: 3
    - GPU type: Tesla T4 / Tesla A16 / GTX 1070TI

## Сhoosing the best model

- Training params:
    - Batch size: 16
    - Image size: 640x640
    - Epochs: 3

| Model   | Precision | Recall | mAP@[.5] | mAP@[.5:.95] |
|---------|-----------|--------|----------|--------------|
| yolov7  | 0.9       | 0.683  | 0.816    | 0.476        |
| yolov5m | 0.908     | 0.814  | 0.876    | 0.485        |
| yolov5s | 0.82      | 0.563  | 0.66     | 0.277        |
| yolov5x | 0.83      | 0.795  | 0.878    | 0.43         |


- Params yolo7 after 10 epochs:

| Model   | Precision | Recall | mAP@[.5] | mAP@[.5:.95] |
|---------|-----------|--------|----------|--------------|
| yolov7  | 0.948     | 0.888  | 0.95     | 0.629        |


## Prediction speed

This algorithm processes up to 12 images (1024x1024)
per second on gpu NVIDIA GTX 1070TI with the YOLO7 model. 
This model is chosen as an easy and fast solution. 
Fast learning speed and easy scalability.


## Tree
``` shell
.gitignore
LICENSE.md
Pipfile
Pipfile.lock
README.md
detect.py
inference
   |-- images
   |   |-- example.png
   |   |-- example1.png
   |   |-- example2.png
   |   |-- example3.png
   |   |-- example4.png
   |-- video
   |   |-- example.MOV
   |   |-- example2.mp4
   |-- presentation
   |   |-- pilot_1.pptx
models
   |-- __init__.py
   |-- common.py
   |-- experimental.py
   |-- yolo.py
notebooks
   |-- train.ipynb
requirements.txt
utils
   |-- __init__.py
   |-- activations.py
   |-- add_nms.py
   |-- autoanchor.py
   |-- aws
   |-- datasets.py
   |-- general.py
   |-- google_app_engine
   |-- google_utils.py
   |-- loss.py
   |-- metrics.py
   |-- plots.py
   |-- torch_utils.py
   |-- wandb_logging
``` 
## Contributors
1. Шакиров Ренат
2. Набатчиков Илья
3. Могилевский Саша

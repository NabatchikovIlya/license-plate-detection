# License Plate Detection based on Yolov7 and OCR systems: PyTesseract, EasyOCR, Attention OCR (soon)


## Installation

``` shell
# apt install required packages
sudo apt update
sudo apt install -y zip htop screen libgl1-mesa-glx tesseract-ocr pipenv
  
# clone repo:
git cline https://github.com/NabatchikovIlya/license-plate-detection.git

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

## Contributors
1. Шакиров Ренат
2. Набатчиков Илья
3. Могилевский Саша

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
   |   |-- test_range.jpg
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

# Long-Short Match for Lost Control in UAV Multi-Object Tracking

## Environment:
```
conda create -n LSMTrack python=3.8 -y && conda activate LSMTrack
python -m pip install -r requirements.txt
python setup.py develop
python -m pip install cython
python -m pip install 'git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
python -m pip install cython_bbox
```

## Dataset
Download the [VisDrone](https://github.com/VisDrone/VisDrone-Dataset) and [UAVDT](https://sites.google.com/view/grli-uavdt/%E9%A6%96%E9%A1%B5), and put them under <LSMTrack_HOME>/datasets in the following structure:
```
datasets   
   |——————VisDrone-MOT
   |        └——————VisDrone2019-MOT-train
   |        └——————VisDrone2019-MOT-val
   |        └——————VisDrone2019-MOT-test-dev
   └——————UAVDT
            └——————uavdt-test
            └——————uavdt-train
```

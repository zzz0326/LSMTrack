# Long-Short Match for Lost Control in UAV Multi-Object Tracking

## Environment
```
conda create -n LSMTrack python=3.8 -y && conda activate LSMTrack
python -m pip install -r requirements.txt
python setup.py develop
python -m pip install cython
python -m pip install 'git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
python -m pip install cython_bbox
```

## Dataset
Download the [VisDrone-MOT](https://github.com/VisDrone/VisDrone-Dataset) and [UAVDT](https://sites.google.com/view/grli-uavdt/%E9%A6%96%E9%A1%B5), and put them under the <DataPath> in the following structure:
```
DataPath   
   |——————VisDrone-MOT
   |        └——————VisDrone2019-MOT-train
   |        └——————VisDrone2019-MOT-val
   |        └——————VisDrone2019-MOT-test-dev
   └——————UAVDT
            └——————uavdt-test
            └——————uavdt-train
```

## Pre-trained weights
### Detector weight
The detector [weight](https://drive.google.com/drive/folders/1MTtu_gbvK7akKjr3cLNlX28L80fcSFQV) of VisDrone-MOT comes from [u2mot](https://github.com/alibaba/u2mot).

The weight corresponding to UAVDT is obtained from this [link](https://drive.google.com/file/d/19Uvi5d3qSkxmixIXPOcLAm-dh_2YjWo_/view?usp=sharing).
### Tracker weight
| Benchmark |  Weights |
|:---------:|:--------:|
|  VisDrone |  |
|   UAVDT   |  |

## Tracking
* **Test on VisDrone**
```
python tools/track_VisDrone.py <DataPath>/VisDrone2019-MOT-test-dev/sequences --benchmark VisDrone -f exps/example/LSMTrack/yolox_x_u2mot_uavdt.py -c <VisDrone-Detetcor-Weight> --device 1 --fp16 --fuse --cmc-method file --cmc-file-dir VisDrone/test-dev
```
* **Test on UAVDT**
```
python tools/track_UAVDT.py <DataPath>/uavdt_test/sequences --benchmark UAVDT -f exps/example/LSMTrack/yolox_x_u2mot_uavdt.py -c <UAVDT-Detetcor-Weight> --device 1 --fp16 --fuse --cmc-method file --cmc-file-dir UAVDT/test-dev
```

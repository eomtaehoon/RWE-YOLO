# RWE-YOLO
YOLO using Row-wise exposure
paper - [TBD]()

## Performance
TBD

## Setup
``` shell
git clone https://github.com/eomtaehoon/RWE-YOLO.git
cd RWE-YOLO
```
Clone [YOLOv7](https://github.com/WongKinYiu/yolov7) and [YOLOv9](https://github.com/WongKinYiu/yolov9)
``` shell
cp yolov7_utils/datasets.py yolov7/utils/datasets.py
cp yolov9_utils/dataloaders.py yolov9/utils/dataloaders.py
```
## Testing
Evaluating YOLOv7
``` shell
# Evaluating YOLOv7 Models Under Brightness Variations
python test_yolov7.py --data yolov7/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights yolov7/yolov7.pt --name yolov7_brightness_val --brightness 1.0

# Evaluating YOLOv7 Models with Row-Wise Exposure Under Brightness Variations
# python test_yolov7.py --data yolov7/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights yolov7/yolov7.pt --name yolov7_rwe_brightness_val --brightness 1.0 --rwe

# Evaluating YOLOv7 Models with Multi-Exposure HDR Under Brightness Variations
# python test_yolov7.py --data yolov7/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights yolov7/yolov7.pt --name yolov7_hdr_brightness_eval --brightness 1.0 --hdr

# Evaluating YOLOv7 Models with Multi-Exposure HDR and Blur Under Brightness Variations
# python test_yolov7.py --data yolov7/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights yolov7/yolov7.pt --name yolov7_hdr_blur_brightness_eval --brightness 1.0 --hdr --blur 3
```
Evaluating YOLOv9
``` shell
# Evaluating YOLOv9 Models Under Brightness Variations
python val_yolov9.py --data yolov9/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.7 --device 0 --weights 'yolov9//yolov9-c-converted.pt' --save-json --name yolov9_c_c_640_val --brightness 1.0

# Evaluating YOLOv9 Models with Row-Wise Exposure Under Brightness Variations
# python val_yolov9.py --data yolov9/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.7 --device 0 --weights 'yolov9//yolov9-c-converted.pt' --save-json --name yolov9_c_c_640_val --brightness 1.0 --rwe

# Evaluating YOLOv9 Models with Multi-Exposure HDR Under Brightness Variations
# python val_yolov9.py --data yolov9/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.7 --device 0 --weights 'yolov9//yolov9-c-converted.pt' --save-json --name yolov9_c_c_640_val --brightness 1.0 --hdr

# Evaluating YOLOv9 Models with Multi-Exposure HDR and Blur Under Brightness Variations
# python val_yolov9.py --data yolov9/data/coco.yaml --img 640 --batch 32 --conf 0.001 --iou 0.7 --device 0 --weights 'yolov9//yolov9-c-converted.pt' --save-json --name yolov9_c_c_640_val --brightness 1.0 --hdr --blur 3
```
## Training
Training YOLOv7
``` shell
# Training YOLOv7 Models with Row-wise Exposure
python train_yolov7.py --workers 8 --device 0 --batch-size 32 --data yolov7/data/coco.yaml --img 640 640 --cfg yolov7/cfg/training/yolov7.yaml --weights '' --name yolov7-RWE --hyp data/hyp.scratch.p5.yaml --rwe 0.5
```
Training YOLOv9
``` shell
# Training YOLOv9 Models with Row-wise Exposure
python train_yolov9.py --workers 8 --device 0 --batch 32 --data yolov7/data/coco.yaml --img 640 --cfg yolov7/models/detect/gelan-c.yaml --weights '' --name gelan-c-RWE --hyp hyp.scratch-high.yaml --min-items 0 --epochs 500 --close-mosaic 15 --rwe 0.5
```
## Acknowledgements

<details><summary> <b>Expand</b> </summary>

* [https://github.com/WongKinYiu/yolov7](https://github.com/WongKinYiu/yolov7)
* [https://github.com/WongKinYiu/yolov9](https://github.com/WongKinYiu/yolov9)

</details>

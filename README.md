
yolov5-car-ShuffleV2:

add ShuffleV2   backbone  yolov5n.yaml

train :

python  train.py  --data  data/plat.yaml  --cfg   models/yolov5n.yaml  --batch-size 32  --weights  runs/train/exp72/weights/last.pt  --img-size 352

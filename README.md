
yolov5-car-ShuffleV2:

add ShuffleV2   backbone  yolov5n.yaml

train :

python  train.py  --data  data/plat.yaml  --cfg   models/yolov5n.yaml  --batch-size 32  --weights  runs/train/exp72/weights/last.pt  --img-size 352


---> onnx 
 python  models/export.py   --weights  runs/train/exp73/weights/best.pt  --img 352 --batch 1
 
python -m onnxsim   runs/train/exp73/weights/best.onnx carplatesim.onnx
Simplifying...
Checking 0/3...
Checking 1/3...
Checking 2/3...
Ok!

-->ncnn 

./onnx2ncnn carplatesim.onnx  carplatesim.param  carplatesim.bin

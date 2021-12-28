
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

--》  
carplatesim.param   Reshape       Reshape_546              1 1 989 1007 0=-1 1=14 2=3      0=-1  importance



ncnn.infer:

note:  x ,y ,dw,dh  conf x1,y1, x2,y2, x3,y3,x4,y4     sigmoid 

good luck 

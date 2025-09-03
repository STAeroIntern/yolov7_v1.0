Download the lastest weight here:
https://drive.google.com/file/d/1PWmYJ0Wv0a94BDnGjEBmR_wykvTiJqIx/view?usp=drive_link
# finetune p5 models
python train.py --workers 8 --device 0 --batch-size 32 --data data/custom.yaml --img 640 640 --cfg cfg/training/yolov7-custom.yaml --weights 'yolov7_training.pt' --name yolov7-custom --hyp data/hyp.scratch.custom.yaml

# finetune p6 models
python train_aux.py --workers 8 --device 0 --batch-size 16 --data data/custom.yaml --img 1280 1280 --cfg cfg/training/yolov7-w6-custom.yaml --weights 'yolov7-w6_training.pt' --name yolov7-w6-custom --hyp data/hyp.scratch.custom.yaml

Inference
On video:

python detect.py --weights yolov7.pt --conf 0.25 --img-size 640 --source yourvideo.mp4
On image:

python detect.py --weights yolov7.pt --conf 0.25 --img-size 640 --source inference/images/horses.jpg

# 训练指令
dota数据集转yolo格式
python train.py --img 640 --batch 16 --epochs 5 --data ./DOTA/datasets/DOTA.yaml --cfg ./models/DOTAyolov5s.yaml
python train.py --img 640 --batch 16 --epochs 5 --data ./data/coco128.yaml --cfg ./models/yolov5s.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3ECA.yaml --weights ./runs/train/exp20/weights/best.pt
--resume ./runs/train/exp20/weights/last.pt
python train.py --img 640 --batch 16 --epochs 1 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5s.yaml
python train.py --img 640 --batch 16 --epochs 5 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3CBAM.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3CBAM.yaml
python detect.py --weights best.pt --source ./data/images
ECA注意力机制
# class names
names: ['small-vehicle', 
'large-vehicle', 
'plane', 
'storage-tank', 
'ship', 
'harbor',
 'ground-track-field', 
'soccer-ball-field',
 'tennis-court', 
'swimming-pool', 
'baseball-diamond', 
'roundabout', 
'basketball-court', 
'bridge', 
'helicopter', 
'container-crane']

yolov5原模型 100轮 exp
DOTAYOLOv5s summary: 157 layers, 7053277 parameters, 0 gradients, 15.9 GFLOPs
                        Class     Images  Instances          P          R      mAP50   mAP50-95: 100%|██████████| 7/7 [00:07<00:00,  1.08s/it]
                            all        206       3604      0.683      0.631      0.647      0.411
                          small-vehicle        206       1351      0.444      0.655      0.597      0.351
                           large-vehicle        206        543      0.577      0.899      0.773      0.501
                        plane        206        366      0.813       0.97       0.95      0.718
                         ship        206        423      0.374      0.442       0.39      0.219
                      harbor        206        190      0.478      0.511      0.469      0.245
      ground-track-field        206          8      0.355      0.375      0.319      0.177
         soccer-ball-field        206         31      0.662      0.631      0.689      0.393
               tennis-court        206        229      0.846      0.956      0.964      0.874
          swimming-pool        206        365      0.668       0.77      0.665      0.275
      baseball-diamond        206         51      0.823      0.725      0.699      0.315
                    roundabout        206          9      0.841          1      0.995      0.682
            basketball-court        206         14          1      0.273      0.711      0.503
                         helicopter        206         24          1          0      0.188     0.0848
Results saved to runs\train\exp

SimAM注意力机制 50轮 exp3
DOTAYOLOv5s summary: 159 layers, 7053277 parameters, 0 gradients, 15.9 GFLOPs
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100%|██████████| 7/7 [00:07<00:00,  1.12s/it]
                   all        206       3604      0.701       0.58      0.581       0.33
         small-vehicle        206       1351      0.495      0.625      0.584      0.321
         large-vehicle        206        543      0.533       0.88      0.712      0.396
                 plane        206        366      0.859      0.956      0.948      0.667
                  ship        206        423      0.496      0.261      0.303      0.138
                harbor        206        190      0.522      0.284      0.308      0.122
    ground-track-field        206          8      0.915       0.25      0.446     0.0964
     soccer-ball-field        206         31       0.84      0.507      0.704       0.36
          tennis-court        206        229      0.887      0.934      0.939       0.79
         swimming-pool        206        365      0.709      0.784      0.667      0.272
      baseball-diamond        206         51      0.552      0.627      0.576      0.232
            roundabout        206          9       0.93          1      0.995       0.68
      basketball-court        206         14       0.38      0.429      0.332      0.198
            helicopter        206         24          1          0     0.0433     0.0173

python train.py --img 640 --batch 8 --epochs 50 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTASimAMyolov5s.yaml
ECA
SimAM注意力机制 50轮 exp7
DOTASimAMYOLOv5s summary: 165 layers, 7053277 parameters, 0 gradients, 15.9 GFLOPs
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100%|██████████| 13/13 [00:07<00:00,  1.67it/s]
                   all        206       3604      0.565       0.53      0.512      0.271
         small-vehicle        206       1351      0.442      0.611      0.566      0.298
         large-vehicle        206        543      0.487      0.868      0.678      0.347
                 plane        206        366      0.803      0.954      0.951      0.652
                  ship        206        423      0.312      0.251      0.218        0.1
                harbor        206        190      0.327      0.274      0.215     0.0677
    ground-track-field        206          8      0.949        0.5      0.567      0.136
     soccer-ball-field        206         31      0.422       0.29      0.347      0.149
          tennis-court        206        229      0.837      0.926      0.932      0.759
         swimming-pool        206        365      0.583      0.751      0.607      0.233
      baseball-diamond        206         51      0.463      0.608      0.573      0.216
            roundabout        206          9      0.719      0.856       0.89      0.518
      basketball-court        206         14          0          0     0.0603     0.0261
            helicopter        206         24          1          0     0.0576     0.0188
Results saved to runs\train\exp7


请问博主，我先训练了100个epoch，还想接着训练怎么办呀
可以接着上一轮继续训练 应该是-resume 加上最后一个权值路径 last.pt 你可以尝试一下

python train.py --img 640 --batch 16 --epochs 50 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAM.yaml
python train.py --img 640 --batch 16 --epochs 50 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sECA.yaml

1.删除3 5 6 7 8 9.....
2.将4改为3
3.随机挑选2000 800数据集

2023/7/26
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5s.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sSE.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sSimAM.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sECA.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCoordAtt.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAM.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSAConv.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMDCNConv.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMDSConv.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMCoordConv.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCoordAttCoordConv.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMdyhead.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSPPCSPC.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSPPCSPC_group.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMASPP.yaml
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMBasicRFB.yaml

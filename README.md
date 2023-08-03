# 训练指令
# datesets

将下载好的数据集放在文件夹（test-main）中，在终端输入运行指令即可运行。

Put the downloaded dataset in the folder (test-main) and enter the run command in the terminal to run.

DOTA_split： 链接：https://pan.baidu.com/s/1dunBf9Ib5yNqbNJmszIq0A 提取码：54p2

# 改进模型（CBAM注意力机制+EIOU损失函数+CoordConv卷积）训练指令
python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMCoordConv.yaml

# 损失函数 CIOU / SIOU / EIOU / WIOU
utils/loss.py utils/metrics.py

# 基础训练指令
python train.py --img 640 --batch 16 --epochs 5 --data ./DOTA/datasets/DOTA.yaml --cfg ./models/DOTAyolov5s.yaml

python train.py --img 640 --batch 16 --epochs 5 --data ./data/coco128.yaml --cfg ./models/yolov5s.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3ECA.yaml --weights ./runs/train/exp20/weights/best.pt
--resume ./runs/train/exp20/weights/last.pt

python train.py --img 640 --batch 16 --epochs 1 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5s.yaml

python train.py --img 640 --batch 16 --epochs 5 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3CBAM.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./split/DOTA_split.yaml --cfg ./models/DOTAyolov5sC3CBAM.yaml

python detect.py --weights best.pt --source ./data/images

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

# 2023/7/26
# 注意力机制 SE / SimAM / ECA / CoordAtt / CBAM

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5s.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sSE.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sSimAM.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sECA.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCoordAtt.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAM.yaml

# 卷积 SAConv / DCNConv / DSConv / CoordConv 

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSAConv.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMDCNConv.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMDSConv.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMCoordConv.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCoordAttCoordConv.yaml

# 检测头 dyhead

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMdyhead.yaml

# 空间金字塔池化改进 SPP / SPPF / ASPP / RFB / SPPCSPC

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSPPCSPC.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMSPPCSPC_group.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMASPP.yaml

python train.py --img 640 --batch 16 --epochs 100 --data ./DOTA_split/DOTA_split.yaml --cfg ./models/DOTAyolov5sCBAMBasicRFB.yaml

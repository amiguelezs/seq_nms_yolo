# Seq_nms_YOLO

#### Membres: Yunyun SUN, Yutong YAN, Sixiang XU, Heng ZHANG
#### Modified by: Alejandro Miguelez and Guillermo Recio

---

## Introduction

![](img/index.jpg) 

This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.

## Steps

1. Download the code from this repository in .zip format or by running `git clone https://github.com/amiguelezs/seq_nms_yolo.git`
2. If the .zip option was chosen in the previous step, unzip the file by running `unzip seq_nms_yolo-master.zip`
3. Enable execution permissions to the folder by running `chmod -R 755 seq_nms_yolo-master`
4. Go to the directory by running `cd seq_nms_yolo-master`
5. Activate anaconda by running `source activate`
6. Create the virtual environment using the available file lab2_DL4VSP.yml by running `conda env create -f lab2_DL4VSP.yml`
7. Activate the environment by running `conda activate lab2_DL4VSP`
8. Modify the Makefile acording to you environment. By default:
   * GPU=1		   # 0 if your pc doesn't support CUDA
   * CUDNN=0		# 1 if your pc does support CUDNN
   * OPENCV=1	   # 0 if your pc doesn't support OPENCV
10. Make the project running the Makefile by running `make`
11. Download yolo.weights and tiny-yolo.weights by running `wget https://pjreddie.com/media/files/yolo.weights` and `wget https://pjreddie.com/media/files/yolov2-tiny-voc.weights`
12. Go to the video folder by running `cd video`
13. In the video folder run `python video2img.py -i v_BalanceBeam_g18_c01.avi` and `python get_pkllist.py`. Here the example video v_BalanceBeam_g18_c01.avi has been used but it can be changed to any other video from the video folder.
14. Return to the previous folder by running `cd ..`
15. Run the next command to generate output images in video/output folder: `python yolo_seqnms.py`
16. If you want to reconstruct a video from these output images, you can go to the video folder and run `python img2video.py -i output`
17. You will see output.mp4 file with detection results in video folder and detection frames in video/output

## Use Yolov2 without Seq-NMS

In order to deactivate Seq-NMS post-processing add to the `python yolo_seqnms.py` execution `--seq_nms 0` flag.
If we want to deactivate the NMS delating non relevant detections add to the execution `--nms 0` flag.

Final execution for Yolov2 only: `python yolo_seqnms.py --seq_nms 0 --nms 0`

## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).

Videos come from [UCF-101](https://www.crcv.ucf.edu/data/UCF101.php) dataset.

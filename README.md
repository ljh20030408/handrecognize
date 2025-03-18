# hand-keras-yolo3-recognize
手语图像识别系统设计

一个基于人体姿态研究的手语图像识别系统。根据OpenPose人体姿态开源模型和YOLOv3自训练手部模型检测视频和图像，再把数字特征进行分类器模型预测，将预测结果以文本形式展现出来。

预期是通过手机移动端对视频进行采集处理并应用

# 软硬件环境
基于人体姿态的手语图像识别系统采用了软硬件相结合的方法。硬件部分主要是用于采集手语图像的单目摄像头。软件部分主要是通过ffmpeg对视频图像进行处理，然后在Anaconda下配置Python3.6的开发环境，再结合Cmake编译OpenPose模型，最后在VScode编译器中结合OpenCV中的图像算法，实现了对手语图像识别系统所有程序的编译，通过wxFromBuilder框架整合设计了系统主界面。
## 硬件环境
手语视频图像采集主要采用的硬件设备有笔记本电脑摄像头和手机摄像头。
程序运行硬件环境详细参数如下：

（1）操作系统：Windows10家庭版，64bit

（2）GPU：Intel(R) Core(TM) i5-8300H，主频：2.30GHz

（3）内存：8G

## 软件环境
（1） 视频处理工具：ffmpeg-20181115

（2） 集成开发环境：Microsoft Visual Studio Code、Anaconda3

（3） 界面设计工具：wxFromBuilder

（4） 编程语言环境：python3.6
# 系统功能设计
一个基于人体姿态研究的手语图像识别系统。根据OpenPose人体姿态开源模型和YOLOv3自训练手部模型检测视频和图像，再把数字特征进行分类器模型预测，将预测结果以文本形式展现出来。

基于人体姿态的手语图像识别系统是由多模块组成的，主要分为训练模块和识别模块两个部分。
## 1. 视频帧处理
## 2. OpenPose人体姿态识别
## 3. yolov3手部模型训练
项目结构主要分为两大部分：YOLOv3深度模型训练部分和YOLOv3和OpenPose手语姿态识别部分。

## 4. 人体姿态数字特征提取

基于 keras的yolo3训练部分项目结构如下表所示：


keras-yolo3训练项目结构:


名称	|类型	|内容
|--|--|--|
yolov3.weights	|配置文件|	权重文件
yolov3.cfg	|配置文件|	配置文件
convert.py|	函数|	模型格式转换
train.py|	函数	|模型训练
voc_annotation.py	|函数	|voc格式标签
yolo_annotations.py	|函数|	yolo格式标签
yolo.py 	|函数	|yolo方法接口
model_data	|文件夹	|参数配置
nets	|文件夹	|yolo网络
utils	|文件夹	|图片加载工具类
VOCdevkit	|文件夹	|VOC格式数据集
logs	|文件夹|	h5训练的模型生成目录

其中logs文件夹用于存放训练好的模型，VOCdevkit用于存放图片和标注信息。

model_data文件夹内容:

名称	|类型|	内容
|--|--|--|
test.txt	|文本|	测试图片信息
train.txt	|文本	|训练图片信息
val.txt	|文本|	训练测试图片信息
voc_class.txt|	文本	|标签样本名称
yolo_anchors.txt	|文本|	先验参数
yolo_weights.h5|	模型	|权重文件

nets文件夹内容:

名称	|类型	|内容
|--|--|--|
darknet53.py	|函数|	卷积神经网络结构
loss.py	|函数|	计算图像检测效果
yolo3.py	|函数	|Yolov3网络识别算法

## 5.beyes分类识别

识别部分代码结构:

名称|	类型	|内容
--|--|--
filesUtils	|文件夹|	文件批量处理
model|	文件夹|	模型
pose	|文件夹	人体姿态识别相关算法
ui	|文件夹	|界面设计
yolo3	|文件夹	|Yolov3手部识别相关算法
beyes.py	|函数|	分类模型算法
getKeyFrame.py|	函数|	提取视频关键帧
pose_hand.py	|函数	|人姿和手部识别综合接口
UI.py	|函数|	可视化界面
yolo.py|	函数	|手部识别接口
SaveImg_graphviz.py	|函数	|绘制函数关系图

视频文件处理filesUtils文件夹：

名称	|类型	|内容
--|--|--
Image_classification.py|	函数	|图片分类
VideoUtils.py	|函数	|视频压缩、移动、重命名
ImgUtils.py	|函数|	图片压缩、移动、重命名
videoConv.bat	|可执行程序	|视频批量处理可执行程序

模型model文件夹：

文件夹	|名称	|类型|	内容
--|--|--|--
pose_coco|	pose_deploy_linevec.prototxt	|文本	|OpenPose人体姿态参数
-|pose_iter_440000.caffemodel	|模型	|OpenPose人体姿态模型
yolov3|	coco_anchors.txt|	文本|	Yolo手部识别先验参数
--	|voc_classes.txt	|文本|	Yolo手部种类
--	|last1.h5	|模型	|Yolo手部识别模型
||train_model.pkl	|模型	|朴素贝叶斯分类模型

基本算法pose和yolov3文件夹：

文件夹	|名称	|类型	|内容
--|--|--|--
pose	|coco.py	|函数	|人体姿态识别算法
-| data_process.py|	函数	|坐标信息转数字特征算法
yolov3|	model.py|	函数	|手部识别算法
-|utils.py|	函数	|数据格式处理函数


# 使用

1. 配置好相应环境[docs/requirements.txt]

2. 修改相应路径，运行UI_main.py


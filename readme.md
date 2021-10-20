# 目录

- [目录](#目录)
- [项目介绍](#项目介绍)
  - [项目进度](#项目进度)
    - [TEST](#test)
    - [TODO](#todo)
    - [BUG](#bug)
  - [配置环境](#配置环境)
    - [修改 Torch 库(如果 Torch < 1.7.0)](#修改-torch-库如果-torch--170)
  - [重新训练网络权重](#重新训练网络权重)

# 项目介绍

使用基于**YOLOv5**+**siamRPN**的神经网络模型识别**无人机**

运行环境: Nvidia axvier + Ubuntu 18.04 + ROS1 melodic

依赖: pytorch 1.2

## 项目进度

### TEST

- 只用一张图展示
- 发送图片消息

### TODO

- 消除torch的警告SourceChangeWarning

### BUG

- pointgray_camera找不到nodelet包
- 摄像头测试时无法关闭节点

## 配置环境

### 修改 Torch 库(如果 Torch < 1.7.0)

打开 Python 的 Torch 根目录，将 extra 内的文件复制到目录内

## 重新训练网络权重

在github上下载源码，按照教程进行训练。训练完成后执行以下代码将模型转换为旧模型

```python
import torch

model = torch.load('yolov5s.pt') 
torch.save(model,'yolov5s_old.pt',_use_new_zipfile_serialization=False)
``` 
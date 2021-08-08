# 目录

- [目录](#目录)
- [项目介绍](#项目介绍)
  - [项目进度](#项目进度)
    - [TEST](#test)
    - [TODO](#todo)
    - [BUG](#bug)
  - [配置环境](#配置环境)
    - [Xavier 设置功耗模式](#xavier-设置功耗模式)
    - [修改 Torch 库(如果 Torch < 1.7.0)](#修改-torch-库如果-torch--170)
  - [重新训练网络权重](#重新训练网络权重)

# 项目介绍

## 项目进度

### TEST

- Xavier电源线，19v供电

### TODO

- 和正负样本进行对比，大于阈值则继续跟踪
- 曝光问题
- 图像识别置信度太低
  - 重新训练数据集
- 测试角度和距离解算
- 完成发送和订阅
  - 使用主从机
- 摄像头位置不是在车辆正中间
- 消除torch的警告SourceChangeWarning

### BUG

- 找不到nodelet包
- 摄像头测试时无法关闭节点

## 配置环境

### Xavier 设置功耗模式

Jetson AGX Xavier 的功耗模式共有 8 种，分别编号为 0-7，依次为如下：

0. MAXN
1. MODE 10W
2. MODE 15W
3. MODE 30W ALL
4. MODE 30W 6CORE
5. MODE 30W 4CORE
6. MODE 30W 2CORE
7. MODE 15W DESKTOP
   
切换模式可使用命令如下， 如切换到MAXN模式为：

```
sudo nvpmodel -m 0
```

功耗模式的查询可使用命令如下：

```
sudo nvpmodel --query
```

### 修改 Torch 库(如果 Torch < 1.7.0)

打开 Python 的 Torch 根目录，将 extra 内的文件复制到目录内

## 重新训练网络权重

在github上下载源码，按照教程进行训练。训练完成后执行以下代码将模型转换为旧模型

```python
import torch

model = torch.load('yolov5s.pt') 
torch.save(model,'yolov5s_old.pt',_use_new_zipfile_serialization=False)
``` 
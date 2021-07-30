# 项目介绍

## TODO

- 完成发送和订阅
  - 使用主从机
- 测试角度和距离解算
- 跟踪问题
  - 存在检测到错误目标的概率
- 测试参数640->1280
- 摄像头位置不是在车辆正中间
- 摄像头测试时无法关闭节点

## 配置环境

### 修改 Torch 库(如果 Torch<1.7.0)

打开 Python 的 Torch 根目录，将 extra 内的文件复制到目录内

## 重新训练网络权重

在github上下载源码，按照教程进行训练。训练完成后执行以下代码将模型转换为旧模型

```python
import torch

model = torch.load('yolov5s.pt') 
torch.save(model,'yolov5s_old.pt',_use_new_zipfile_serialization=False)
``` 
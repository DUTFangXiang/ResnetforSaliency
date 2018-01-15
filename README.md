# ResnetforSaliency
这是在caffe上基于Deep Residual Network实现显著性目标检测的模型，算法是fine tune训练好的Resnet网络实现的

### 1、caffe版本问题
  该网络实现是基于Pyramid Scene Parsing Network新建的caffe版本实现，其中主要增加了Interp层的功能。

caffe版本下载地址：https://github.com/hszhao/PSPNet； 按流程安装即可。
### 2、训练数据
本人实现是在10000张图片库THUS上训练的，请自行构建train.txt和train_gt01.txt文件，图片和真值图索引，其中所有图片的分类标签都设置为0。
因为我们没有涉及分类，所以分类标签不影响结果。但是请将所有真值图中0/1标识前背景从double类型转为uint8类型存储。
### 3、fine tune原网络
原网络是kaiming he的深度残差网络Resnet。
### 4、文件分布
train.ptototxt描述整体训练网络框架，其中需要将训练数据txt文件路径两个修改成相对应你的路径；

solver.prototxt是网络参数配置文件；

deploy.prototxt是测试网络框架；

trainModel.sh是fine tune训练网络的shell指令，请将对应Resnet的caffemodel修改成自己的路径；

test.m是调用caffe的matlab接口实现测试。其中网络参数是调用训练新生成的caffemodel文件；请修改文件中对应对方的路径。


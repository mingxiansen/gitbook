# GPU加速软件介绍

## 基础架构

要在带有GPU的服务器上跑机器学习程序，需要以下4个软件支持  
- 显卡驱动  
- CUDA
- cuDNN
- 机器学习框架(可以不用框架写程序，不过用框架会方便很多)  

他们之间的依赖关系如下图所示

![架构](../../img/part2/architecture.png)   

首先，软件都需要通过**显卡驱动程序**操作GPU  
其上层的**CUDA**(Compute Unified Device Architecture)是NVIDIA为自家显卡提供的计算库，为更上层的软件提供执行并行计算的接口.比如借助CUDA，你可以用C++很方便的执行矩阵操作之类的运算  

**cuDNN** 由是NVIDIA官方人员编写的专门用于加速神经网络的程序库，提供了各类高度优化的神经网络模型接口，调用Cudnn的接口训练RNN/CNN等网络，会比自己写快很多  

**机器学习框架** 让我们可以用Python等语言编写机器学习程序，在使用GPU加速计算过程时需要上面两个软件的支持


## 如何选择合适的CUDA版本
CUDA和cuDNN有不同版本，我们需要跟剧使用的机器学习框架选择版本  
下面以pytorch和tensorflow为例，分别说明.

### Pytorch的需求
在[Pytorch官网](https://pytorch.org/)的下载界面，你可以看到如下图的提示

![Pytorch Cuda需求](../../img/part2/pytorch-version.png)  

最后一行是CUDA版本的选择，需要跟服务器的CUDA版本一致
请询问学长/学姐服务器的CUDA版本，选择匹配的下载即可，如果服务器还没有安装CUDA，那就选一个最新版本的

### Tensorflow的需求
**Tensorflow** 的要求在[这个链接](https://tensorflow.google.cn/install/install_sources#tested_source_configurations)，不像Pytorch提供了多种选择，每种Tensorflow版本只提供一种编译好的版本

![Tensorflow Cuda需求](../../img/part2/tensorflow-version.png)

没有特殊需求的话,建议安装最新版,截止2018年9月12号,Tensorflow最新版是1.10,虽然上面的图片没有显示它的CUDA版本要求,其实是和1.8一样的,都是CUDA9.0和cuDNN7.1  

这个教程的目的是帮助大家从零配置最新版本的Tensorflow环境,下一节讲解如何安装CUDA和cuDNN  
**但是需要注意的是,目前实验室的三台服务器都安装了cuda9和cuDNN7.1,路径都是/usr/local/cuda9.0-cudnn7.1,新来的学弟学妹可以不用自己安装CUDA和cuDNN了,跳过安装步骤,直接看最后的配置步骤就可以**

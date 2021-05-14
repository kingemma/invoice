
# Anaconda3 install multiple versions Python 
	https://appuals.com/could-not-find-a-version-that-satisfies-the-requirement-for-tensorflow/

	conda install python=3.6.4
	conda create -n python3.6
	conda activate python3.6
	Change folder to D:\Evan\2-TestGitHub\invoice

	利用Anaconda Navigator (Anaconda3)新建Python环境，
	利用conda activate python3.6
	然后切换到项目目录运行 安装 
	pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple 


 File "app.py", line 9, in <module>
    import cv2
  File "D:\Anaconda3\lib\site-packages\cv2\__init__.py", line 5, in <module>
    from .cv2 import *
ModuleNotFoundError: No module named 'cv2.cv2'

(python3.6) D:\Evan\2-TestGitHub\invoice>pip uninstall opencv-python opencv-contrib-python

# 增值税发票识别 
  识别type：增值税电子普通发票，增值税普通发票，增值税专用发票；识别字段为：发票代码、发票号码、开票日期、校验码、税后金额等
## 环境
   1. python3.5/3.6
   2. 依赖项安装：pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple 
   3. 有GPU环境的可修改安装requirements.txt对应版本的tensorflow-gpu，config.py文件中控制GPU的开关
   4. GPU 安装
   https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_local
## 模型架构
    YOLOv3 + CRNN + CTC
   
## 模型
   1. 模型下载地址：链接：https://pan.baidu.com/s/1bjtd3ueiUj3rt16p2_YQ2w
   2. 将下载完毕的模型文件夹中的文件拷贝到models目录并放置于项目根目录下
## 服务启动
   1. python3 app.py
   2. 端口可自行修改
   3. 服务调用地址：http://*.*.*.*: [端口号]/invoice-ocr，例：http://127.0.0.1:11111/invoice-ocr
## 测试demo
   1. 测试工具：postman，可自行下载安装
   2. 增值税电子普票测试结果
   
![Image text](https://github.com/guanshuicheng/invoice/blob/master/test-invoice/%E7%94%B5%E5%AD%90%E5%8F%91%E7%A5%A8-test.png)
   
   3. 增值税专用普票测试结果
   
![Image text](https://github.com/guanshuicheng/invoice/blob/master/test-invoice/%E5%A2%9E%E5%80%BC%E7%A8%8E%E4%B8%93%E7%94%A8%E5%8F%91%E7%A5%A8-test.png)

   4. 增值税普通普票测试结果

![Image text](https://github.com/guanshuicheng/invoice/blob/master/test-invoice/%E5%A2%9E%E5%80%BC%E7%A8%8E%E6%99%AE%E9%80%9A%E5%8F%91%E7%A5%A8-test.jpg)
   
## 后期开发计划

后期逐步将模型迁移至TF-serving...

## 参考
chineseocr https://github.com/chineseocr/chineseocr

## 报错
	2020-09-20 21:31:45.455714: W tensorflow/stream_executor/platform/default/dso_loader.cc:59] Could not load dynamic library 'libcudart.so.10.1'; dlerror: libcudart.so.10.1: cannot open shared object file: No such file or directory
	2020-09-20 21:31:45.455738: I tensorflow/stream_executor/cuda/cudart_stub.cc:29] Ignore above cudart dlerror if you do not have a GPU set up on your machine.

原文链接：https://blog.csdn.net/qq_41683065/article/details/108702408
看报错信息也能看出来时GPU的问题。

查阅资料后时GPU的版本与TensorFlow的版本不一致。
https://tensorflow.google.cn/install/source#gpu

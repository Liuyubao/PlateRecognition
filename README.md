

简介
--

本文基于HyperLPR进行修改，完整代码参考https://github.com/Liuyubao/PlateRecognition

HyperLPR是一个使用深度学习针对对中文车牌识别的实现，与较为流行的开源的其他框架相比，它的检测速度和鲁棒性和多场景的适应性都要好于目前开源的框架，HyperLPR可以识别多种中文车牌包括白牌，新能源车牌，使馆车牌，教练车牌，武警车牌等。 

使用的目标检测器是基于OpenCV的Haar级联分类器。其速度也达到了不错的效果，对于移动端的大车牌基本可以实时定位。

使用了大概4700张正样本车牌车12000张负样本进行了分类器训练。



训练的方法
-----

使用了OpenALPR的Train - Detector，来进行训练Opencv的Haar级联分类目标检测器。 
正样本可以通过手动crop或者使用easypr或者hyperlpr的模块进行crop裁剪。 
负样本在train detector目录下已经包含了一些基本的负样本，我们在多次训练后发现，使用这些负样本训练出来的检测器在垂直边缘密集的地方误检特别高。 这时候我们就要使用类似于Hard Sample Mining的策略 将这些部分的误检区域crop出来。加入到分类器中训练。 

检测器的使用很简单。使用opencv中的cascadeclassifier进行多尺度检测即可。 

可识别和待支持的车牌的类型
-------------

 - 单行蓝牌
 - 单行黄牌
 - 新能源车牌
 - 白色警用车牌
 - 使馆/港澳车牌
 - 教练车牌
 - 武警车牌


代码实现
----

进入对应目录可直接运行 plateRecognition.py 文件。

![这里写图片描述]( https://img-blog.csdn.net/20180621234815734?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1l1YmFvTG91aXNMaXU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70 )

基于HyperLPR进行修改，完整代码参考https://github.com/Liuyubao/PlateRecognition

如有疑问，欢迎留言或微信咨询：523331232

结果展示
----

【单个车牌】

![这里写图片描述](https://img-blog.csdn.net/20180621235403140?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1l1YmFvTG91aXNMaXU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![这里写图片描述](https://img-blog.csdn.net/20180621235418911?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1l1YmFvTG91aXNMaXU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


【多个车牌】

![这里写图片描述](https://img-blog.csdn.net/20180621235618458?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1l1YmFvTG91aXNMaXU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![这里写图片描述](https://img-blog.csdn.net/2018062123563563?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1l1YmFvTG91aXNMaXU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


【完整代码参考https://github.com/Liuyubao/PlateRecognition 】

【如有疑问，欢迎留言或微信咨询：523331232】

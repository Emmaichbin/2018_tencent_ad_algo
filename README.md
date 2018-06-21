
# 2018腾讯广告算法大赛

![](./assets/banner.png)


*******

### 首先，大标题感谢我的辉哥[@Walter000](https://github.com/Walter000)，他拉着我一起参加了比赛，不然我也不知道我在哪里玩泥巴呢
********

### 成绩
* 初赛：47
* 复赛：139（没机器，复赛前一周租了200G内存，1060显卡的机器，但是时间完全来不及，连复现初赛的成绩都来不及），所以复赛基本就是放弃的状态

吐槽下：辉哥似乎学的很多，什么都懂，但是实际的结果却总是拿不出来🙄，就连初赛的成绩也是我拿了3，4台机器，然后一直跑模型，最后加上辉哥的神级submission，模型融合到了7559，混到了一张证书。


###目录结构
项目下有四个目录：

* lgb_libsvm
* ffm代码
* deep_ffm代码
* 开源baseline

#### lgb_libsvm
lgb_libsvm下的代码是使用libsvm格式进行lgb训练和预测的代码，这个目录下就是我的写的代码了，ffm和deepffm的则是辉哥整理和编写的代码
	
* degub文件夹：测试csv转化成libsvm的例子的文件夹
* demo文件夹：小样本demo文件夹
	* twofile：将两个csv文件拼接然后转化为libsvm文件
* feature_engineering：基于libsvm格式，lgb去选特征，验证特征工程是否有效
	* offline_datasets：线下测试的数据文件夹(train_test_split为编译过的可执行性文件，chmod +x ，然后./train_test_split就能看到用法，实验室的大佬用C++写的，速度特别快)
* iioiio：实验室大佬c++写的数据集验证集划分
* lgb_config：lgb训练参数文件
* Ljh：辉哥整理的特征工程代码
* shell_command：训练流程自动化shell脚本(最后来不及，没用到，也没写完)
* submission：提交结果文件夹

#### 开源baseline
[bryan大佬](https://blog.csdn.net/Bryan__/article/details/79623239)的开源，帮助了很多跟我一样的小白，在此表示感谢，把baseline吃透，包括one-hot和CountVector，然后对着sklearn的源码和例子看一下，就能了解到特征的基本处理流程，baseline的主要知识点如下：


* 数据读取、拼接和转化：原来的4张表拼接成一张表，这里csv转化为pandas的DataFrame，然后使用df(dataframe)进行操作，pandas入门，文件读取和字符串操作(userdata的转化)
* one-hot：**处理离散型数**据，且**相互之间独立没有联系**，由于机器学习中需要用计算机能够表达的形式来表示数据，所以one-hot就是一种处理形式，[简单介绍](https://www.cnblogs.com/lzh-cnblogs/p/3764749.html)（后面再单独写一篇博文介绍下，因为之前看的别人写的都不够全面，包括one-hot的特点，使用意义）
* CountVector：**也是处理离散型数据**，跟BOW（Bog of words）一样
* Lightgbm python接口使用和参数设置
* 参数调整
* Lightgbm模型学习(决策树模型、xgboost等)


#### ffm代码和deepfm
> fm和ffm直接使用xlearn框架，deepfm是属于神经网络即深度学习那块的了，使用tensorflow或者pytorch 

fm和ffm：ffm(filed Factorization Machines)是在fm的基础上改进的，学习资料[美团的技术博客](https://tech.meituan.com/deep-understanding-of-ffm-principles-and-practices.html)、fm([1](http://www.jame-zhang.top/assets/algo/Factorization-Machines-with-libFM.pdf)、[2](http://www.jame-zhang.top/assets/algo/Factorization-Machines-Rendle2010.pdf))和[ffm]()([1](http://www.jame-zhang.top/assets/algo/deep-fm1804.04950.pdf)、[2](http://www.jame-zhang.top/assets/algo/deepFM1703.04247.pdf))的论文，这个主要是辉哥整理的，由于我比较菜，所以到比赛结束了，fm和ffm我都没看，deepffm也一样



Part1 深度学习基础  第3章 神经网络入门

## 神经网络解决实际问题

3种场景：

(1) 二分类问题 yes or no，positive or negative，0 or 1

(2) 多分类问题 cat ,dog or bird，0, 1 or 2 

(3) 回归问题 线性、非线性、注意：logistic回归是个分类算法，2分类问题

###  一、神经网络剖析

![image-20200904105905501](C:\Users\sunyi\AppData\Roaming\Typora\typora-user-images\image-20200904105905501.png)

图中出现了层、优化器、损失值和损失函数、输入输出和真实值、权重等概念

​	(1) 层：基础、多层=neural network=model、权重、变换、专用(dense, conv, rnn, lstm)、搭积木、兼容、自动推导

​	(2) 损失函数和损失值：学习反馈、衡量、成功?   value=loss(pred, ground-truth)

​	(3) 优化器：更新、SGD、Adam..   make use of gradient descent  to update params，decide to how to learn

​	(4) 输入输出和真实值：input data, pred data=output data=network(input data), ground-truth=real data

​	(5) 权值：知识，trainable and need train，input data + network + weights can approach ground-truth

### 二、tensorflow.keras和Kears

![image-20200904111411744](C:\Users\sunyi\AppData\Roaming\Typora\typora-user-images\image-20200904111411744.png)

tensorflow中对keras接口进行了实现，tensorflow的keras有自己的API，和老Keras不是指同一个

link：https://tensorflow.google.cn/versions/r2.1/api_docs/python/tf/keras

使用tensorflow.keras进行开发，详见github主页 link：神经网络训练流程图  xmind

### 三、深度学习工作站

GPU加速运算

1 本地GPU， Nvidia 显卡，算力、cuda、cudnn

2 云GPU

​	(1) google colab  ，need 梯子

​	(2) aws，阿里云

​	(3) 淘宝租服务器

​	(4) 1024gpu，DBC，https://www.1024gpu.top/home

3 工具

​	(1) jupyter notebook  (推荐)

​	(2) pycharm (智能提示)

### 四、实际应用

#### 4.1 二分类

​	电影评论：好评 or 差评，imdb数据集

​	https://blog.csdn.net/jiangpeng59/article/details/77533309/

#### 4.2 多分类

​	衣服图像：10类，fashion mnist数据集 ，也可以是cifar 10 or cifar 100

#### 4.3 回归

​	房价：13个特征，波士顿房价数据集

#### 4.4 总结

 1. 二分类最后一层的激活函数是sigmoid，多分类最后一层的激活函数是softmax，回归问题预测的是个具体的数值，最后一层不加激活函数，否则会限制数值的范围

 2. sigmoid是softmax在二分类的特殊情况

 3. 波士顿数据中不同特征的取值范围不同，要消除量纲的影响，做归一化处理

 4. 图像数据要做归一化处理，有助于神经网络的收敛

 5. 回归问题的损失函数选择mse，评价指标用准确度没有意义，应该使用mae，即平均绝对值误差

 6. k折交叉验证的流程，当k=3时

    ![image-20200904182649560](C:\Users\sunyi\AppData\Roaming\Typora\typora-user-images\image-20200904182649560.png)

    最终取平均分数，才更有意义

    k折交叉验证适用在可用的数据很少，它不会提升很大的模型性能，因为毕竟数据量本身并没有增大

 7. 神经网络的中间神经元个数如果设置过小会导致模型性能下降，因为中间维度太小，导致神经网络无法将前一层的全部有效信息传递到下一层，就会丢失很多有效的信息，导致信息瓶颈

 8. 过拟合是指在训练集上效果很好，而测试集上效果很差，达不到训练集的准确度，网络对于新数据的泛化能力太差，只认识训练过的数据

 9. 解决过拟合的根本是增加数据量，因为这样模型会认识到更多的数据，学习到不同的数据分布模态，增加鲁棒性，当数据量有限的时候，可以使用dropout，L1 or L2正则化，批归一化Batch Normolization等
















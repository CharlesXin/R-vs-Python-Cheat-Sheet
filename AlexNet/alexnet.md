# ImageNet Classification with Deep Convolutional Neural Networks #
Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton; NIPS 2012

这篇论文是对2012 Image Net图像识别竞赛的冠军算法的总结和展示。这个深度卷积神经网络（CNN）由Hinton的得意门生Alex Krizhevsky提出，成为了深度神经网络的开山鼻祖，俗名AlexNet。当然，也许有人会提到LeCun在1998年提出CNN的论文，但他的影响远不及AlexNet，我们在此先按下不表。这个模型在ImageNet竞赛中将120万个高分辨率图像分为了1000类，其前五分错率（对给定图片，模型生成的前五个预测都错）为15.4%，远远高于第二名的模型（前五分错率26.2%）。从这以后，CNN也成为了图像识别竞赛的标配，并逐渐成为业界的宠儿。

AlexNet的结构如下图所示，一共八层，其中前五层是卷积层；其后三层是全连接的网络，最终的输出成用softmax作1000类的分类。
![Alt text](neural_language_model.png)

除了在整体结构上的创新，AlexNet在很多模型细节上也可圈可点。首先它使用了修正线性单元（Rectified linear unit，简写作ReLU），可使模型加速收敛，并且避免了sigmoid函数梯度消失的可能。其次，作者使用了两块GPU来进行并行运算，仅用五天完成了训练。为了防止过拟合上，AlexNet采用了数据增强（Data Argmentaion)技术，对图片进行随机的的裁剪和翻转。之后在对RGB空间进行主成分分析，并加入高斯扰动。作者还引入了Dropout技术，它以0.5的概率将每个隐层神经元的输出设置为零，那么这些神经元也就不参与正向与反向传播，达到生成多种模型结构的目的，并有效减小过拟合。最后，作者使用了集束随机下降（batch SGD）进行模型优化，并选择了非常小的权值衰减（weight decay = 0.0005）。

这篇论文还提出诸如Local Response Normalization, Max-Pooling等技术，但在之后的实践中使用的较少。其主要的贡献如ReLU函数，数据增强，和Dropout技术最终成为了业界和学界的主流，值得大家再细细踹摩一下。

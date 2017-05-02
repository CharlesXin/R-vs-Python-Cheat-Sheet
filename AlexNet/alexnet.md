# ImageNet Classification with Deep Convolutional Neural Networks #
Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton; NIPS 2012

这篇论文是对2012 Image Net图像识别竞赛的冠军算法的总结和展示。这个深度卷积神经网络（CNN）由Hinton的得意门生Alex Krizhevsky提出，成为了深度神经网络的开山鼻祖，俗名AlexNet。当然，也许有人会提到LeCun在1998年提出CNN的论文，但他的影响远不及AlexNet，我们在此先按下不表。这个模型在ImageNet竞赛中将120万个高分辨率图像分为了1000类，其前五分错率（对给定图片，模型生成的前五个预测都错）为15.4%，远远高于第二名的模型（前五分错率26.2%）。从这以后，CNN也成为了图像识别竞赛的标配，并逐渐成为业界的宠儿。

下图给出了AlexNet的结构：
![Alt text](neural_language_model.png)
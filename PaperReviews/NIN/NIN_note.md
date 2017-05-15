## Network In Network ##
Min Lin, Qiang Ch, Shuicheng Yan

Network In Network针对传统CNNs模型在泛化能力不足的问题， 通过增加多层感知器(MLP)和全域平均池化层(global average pooling)，强化了其对非线性特征的学习能力，并显著减小了参数规模，节省了训练时间。其整体结构如下图，包括了三层多层感知卷积层（mlpconv)的叠加与一个平均池化层 。

![Alt text](structure.png)

** 多层感知卷积层（mlpconv） **  

相比使用广义线性模型做滤波器的滤波器的线性卷积层, Netork in Network使用的卷积与多层感知器相结合的非线性结构（在论文中被称作mlpconv)，使其具有更强的抽象与泛化能力。论文作者还提到MLP也应用反向传播算法进行训练，可以无缝融合进深度神经网络的架构中；其本身也是神经网络算法，符合特征在再利用的思想。  
论文中有一句对多层感知卷积层实现的总结很精辟：跨通道的多层感知卷积层层等价于卷积层 + 1×1卷积核（The cross channel parametric pooling layer is also equivalent to a convolution layer with 1x1 convolution kernel）。结合NIN的结构图我们可以理解为，通过使用1x1的卷积核，可以得到的多个特征图（feature map）的线性组合，从而实现特征图在通道个数上的降维。在普通的卷积层之后加上1x1的卷积核，配合激活函数，就可以实现多层感知卷积层的基本结构。这样的结构，也被用在了之后的GoogLeNet中，并扩展出增维的应用，具体可以考文末Aaditya Prakash的文章。

** 全域平均池化层（Global Average Pooling）**  

在多层感知卷积层结构之后，作者使用了全域平均池化层来代替全连接层。对每一个特征图计算其平均数，然后将这些平均数组成一个特征向量，输入到softmax层中进行分类。这样，多层感知卷积层结构输出的每一层特征图就能够对应相应的分类，而特征图的平均（池化）值则能被解释为相应类别的置信度。而移除全连接层，使得参数规模减小，更有利于网络层数的加深。最后，全域平均池化层作为结构性正则项，也有效减小了过拟合。

参考文献：

Chen, Q., Lin, M., & Yan, S. (2013). Network In Network. CoRR, abs/1312.4400.

Prakash, A. (2016) One by One [ 1 x 1 ] Convolution - counter-intuitively useful. http://iamaaditya.github.io/2016/03/one-by-one-convolution/






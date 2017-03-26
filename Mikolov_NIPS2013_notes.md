# Distributed Representations of Words and Phrases and their Compositionality #
Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean, NIPS 2013


传统的word representation一般采用one-hot vector representation, 也就是给定一个词汇表，词汇量为N，那么第k个词就用一个0-1向量表示，[0,0,...,1,0,..0]， 即第k个元素为1，其余均为0。这个表示方法优点是无须训练，缺点就是忽略了词与词之间的在句法及语义上的关系（syntactic and semantic word relationships）。 比如说hotel和motel，它们本身是两个在语义上（sematically）非常相近的词，但是用one-hot vector 来表示的话，它们之间的点乘积为0，或相似性为0. （一般在自然语言处理中我们用cos similarity来表示词与词之间的相似性）。

这篇论文主要介绍了一种利用神经网络来训练word representation 或者叫做word embedding的模型，称作 Skip-gram model。经过这个模型训练出来的word representation能够抓住word在句法及语义上的关系（syntactic and semantic word relationships）。比如 Capital + France = Paris， king - man + woman = queen等等， 这些都是one-hot vector representation 做不到的。另外一个优点就是Skip-gram model训练出来的word representation的维度很低，比如word2vec模型经Google News数据集训练出来的word representation只有300维，相对于one-hot vector（其维度和词汇量相同，对于大的数据集，在100万以上）已经是大大降低维度了。

这篇论文提到的另外一个模型是continuous Bag-of-Words （CBOW）模型，这个模型的目标也是训练出能够抓住word在句法及语义上的关系（syntactic and semantic word relationships）的word representation。相对于Skip-gram，他们两者的训练方法不一样，continuous Bag-of-Words （CBOW）用周围的word来预测中心的word，而Skip-gram正好相反，用中心的word去预测周围的word。

另外，这篇论文还介绍了几种能够加快模型训练过程的方法，向下采样法（subsampling）和负面采样法（negative sampling）。


-----------

这篇论文是对Tomas Mikolov等人所作Efficient Estimation of Word Representations in Vector Space一文的扩展。本文并未讨论Bag-of-Words （CBOW）模型而更注重于对skip-gram模型在更大数据集上的表现。首先，Mikolov运改进了目标函数并使用了负面采样（Negative Sampling)（这里没太看懂）。 在目标函数中联合概率被简化为多个条件概率的乘积，也就是说给定输入的中心词汇，其输出的词汇是完全独立的。他对高频词进行了筛选，最终提高了模型整体的运算效率。其次，作者简单的词组中的多个词汇标记成同一个token（字符串），也使模型在词组上有较好的表现。最后也是这篇论文最主要的成果是加法组合运算（Additive Compositionality），这将词（词组）与词之间的关系在向量空间中展示了出来。其实最著名的例子便是vec(‘Capital’) + vec(‘France’) = vec(‘Paris)。当然，输出中只有少量例子拥有这样完美的效果，不过多数情况下输出中概率较高的词较合理。

简单地用数学语言解释的话，i和j在同一个上下文（context）中出现的概率应当是与$$$e^{v_i \cdot v_j}$$$成比例。假设我们与第三个词k，那么k与i，j同时出现的概率就应当与$$$e^{v_k \cdot v_i}e^{v_k \cdot v_j} = e^{v_k\cdot(v_j+v_j)}$$$成比例。所以说两个词向量的加所得到的新词向量就有很大概率和它们出现在同一上下文（context）中。在我们刚才的例子中，i是Capital， j是France，那么k就有很大概率是Paris，因为巴黎总是和法国和首都出现在一起的。当然，同时和法国和首都一起出现的词还有很多，所有这只是一种一个看起来最为合理的例子。

参考文献：

Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, and Jeffrey Dean. 2013. Distributed representations of words and phrases and their compositionality. In Proceedings of the 26th International Conference on Neural Information Processing Systems (NIPS'13), C. J. C. Burges, L. Bottou, M. Welling, Z. Ghahramani, and K. Q. Weinberger (Eds.). Curran Associates Inc., , USA, 3111-3119.



# GloVe: Global Vectors for Word Representation #
Jeffrey Pennington, Richard Socher, Christopher D. Manning  


在前几篇论文推荐中，我们主要关注了word2vec这个基于词向量的算法。在这周的论文推荐，我们将推荐一个与其思路相似而且更为新颖的算法利用全局信息提升词向量学习效果, GloVe。 GloVe是由斯坦福的Richard Socher在EMNLP2014发表的，而且更直接的进行了矩阵分解， 并显示词与词之间同时出现的比率（the ratio of the co-occurrence probabilities of two words）。  

在前文中我们提到，word2vec的优化方向是减小 Loss（目标词|上下文）， 也就是减小基于上下文预测目标词的词向量的损失。为了达到这一目标，word2vec运用了一个前馈神经网络并用随机梯度等方法下降进行优化。而GloVe思路是将上下文的全局的词共现矩阵（word co-occurrence）进行了分解而得到词向量。在这一点上，GloVe和Latent Semantic Analysis (LSA)异曲同工，但LSA使用的是词-文档矩阵，而GloVe使用了更为致密的词-词共现矩阵。GloVe的优化目标是使两个词向量间的点积与它们同时出现的的对数和最小。除此之灾，GloVe对高频词和低频词的处理也非常新颖。作者设计了一个权重函数，使得高低频词都不会对模型产生误导。  

GolVe的作者宣称其在同义词任务的准确率比word2vec提升了11%。不过，现今业界的主流仍然是word2vec, GloVe在工程上的实践仍需要更多的探索。  

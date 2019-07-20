---
layout:     post
title:      回环检测-Lightweight Unsupervised Deep Loop Closure
subtitle:   无监督深度学习回环检测-重构hog描述子
date:       2019-07-17
author:     zhufa
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - slam
    - deep learning
---

## 论文引用
总结 16 15 12 是当前场景识别的art_of_state 11 去除了随机物体带来的噪声


卷积神经网络在场景识别上的应用
[10] Z. Chen, O. Lam, A. Jacobson, and M. Milford, “Convo-
lutional neural network-based place recognition,” CoRR,
vol. abs/1411.1509, 2014.

随机放置动态对象
[11] N. Sünderhauf, S. Shirazi, F. Dayoub, B. Upcroft, and
M. Milford, “On the performance of convnet features
for place recognition,” in 2015 IEEE/RSJ International
Conference on Intelligent Robots and Systems (IROS),
Sept 2015, pp. 4297–4304.
对场景中的landmark进行识别来辨认
也无法实时使用
[12] N. Sünderhauf, S. Shirazi, A. Jacobson, F. Dayoub,
E. Pepperell, B. Upcroft, and M. Milford, “Place
recognition with convnet landmarks: Viewpoint-robust,
condition-robust, training-free,” in Robotics: Science and
Systems, Auditorium Antonianum, Rome, July 2015.

用卷积神经网络来提取特征，词带模型来加速查询
[14] Y. Hou, H. Zhang, and S. Zhou, “Bocnf: efficient image
matching with bag of convnet features for scalable and
robust visual place recognition,” Autonomous Robots,
Nov 2017.


依赖Google街景视图中的地理标记的架构
标记三重损失方案的训练图像，其中三元组由两个匹配图像和一个非匹配图像组成
[15] R. Arandjelović, P. Gronat, A. Torii, T. Pajdla, and
J. Sivic, “Netvlad: Cnn architecture for weakly super-
vised place recognition,” IEEE Transactions on Pattern
Analysis and Machine Intelligence, vol. PP, no. 99, pp.
1–1, 2017.

外观不变的地方识别通过歧视性地训练卷积神经元网络
把图像降低维度用128weide维度的向量描述子来描述图像，在场景识别中证明这样是有用的
[16] M. Lopez-Antequera, R. Gomez-Ojeda, N. Petkov, and
J. Gonzalez-Jimenez, “Appearance-invariant place recog-
nition by discriminatively training a convolutional neural
network,” Pattern Recognition Letters, vol. 92, no. Sup-
plement C, pp. 89 – 95, 2017.

专门训练用在场景识别的
[17] Z. Chen, A. Jacobson, N. Sünderhauf, B. Upcroft, L. Liu,
C. Shen, I. Reid, and M. Milford, “Deep learning features
at scale for visual place recognition,” in 2017 IEEE
International Conference on Robotics and Automation
(ICRA), May 2017, pp. 3223–3230.

无监督学习在回环检测的应用
高翔的，使用的是autoencoder,想看看他是这么设计损失函数的
FAB-MAP2.0 更好，但是特征提取很慢
[18] X. Gao and T. Zhang, “Unsupervised learning to detect
loops using deep neural networks for visual SLAM
system,” Autonomous Robots, vol. 41, no. 1, pp. 1–18,
Jan. 2017.

人工设计的特征
28 
Y. Latif, G. Huang, J. Leonard, and J. Neira, “An on-
line sparsity-cognizant loop-closure algorithm for visual
navigation,” in Proc. of Robotics: Science and Systems,
Berkeley, CA, Jul. 12-16 2014.

29
Y. Latif, G. Huang, J. Leonard, and J. Neira, “An on-
line sparsity-cognizant loop-closure algorithm for visual
navigation,” in Proc. of Robotics: Science and Systems,
Berkeley, CA, Jul. 12-16 2014.

30
H. Zhang, F. Han, and H. Wang, “Robust multimodal
sequence-based loop closure detection via structured
sparsity,” in Proc. of Robotics: Science and Systems,
AnnArbor, Michigan, June 2016.

利用卷积神经网络来辨别检测场景（当年的state——of——art）
描述子的维度太大了，用在实时的slam系统里面不太行
[31] P. Sermanet, D. Eigen, X. Zhang, M. Mathieu, R. Fergus,
and Y. Lecun, “Overfeat: Integrated recognition, local-
ization and detection using convolutional networks,” 12
2013.

跨季节的场景识别
忽略一些活跃的部分，比如人？？
[32] C. Kenshimov, L. Bampis, B. Amirgaliyev, M. Arslanov,
and A. Gasteratos, “Deep learning features exception for
cross-season visual place recognition,” Pattern Recogni-
tion Letters, vol. 100, pp. 124 – 130, 2017.

稀疏搜索用在cnn提取的特征上面
[33] D. Bai, C. Wang, B. Zhang, X. Yi, and X. Yang,
“Sequence searching with cnn features for robust and
fast visual place recognition,” Computers and Graphics,
vol. 70, pp. 270 – 280, 2018, cAD/Graphics 2017.

提取和组合强大的功能去噪自动编码器
去噪的在编码器在光照和视角变化上面没有很强悍的鲁棒性
[34] P. Vincent, H. Larochelle, Y. Bengio, and P.-A. Man-
zagol, “Extracting and composing robust features with
denoising autoencoders,” in Proceedings of the 25th In-
ternational Conference on Machine Learning, ser. ICML
’08. New York, NY, USA: ACM, 2008, pp. 1096–1103.

HOG描述子的提出
[36] J. Li, R. M. Eustice, and M. Johnson-Roberson, “High-
level visual features for underwater place recognition,”
in 2015 IEEE International Conference on Robotics and
Automation (ICRA), May 2015, pp. 3652–3659.

image——net上的一个卷积神经网络架构
[39] A. Krizhevsky, I. Sutskever, and G. E. Hinton, “Imagenet
classification with deep convolutional neural networks,”
in Proceedings of the 25th International Conference on
Neural Information Processing Systems - Volume 1, ser.
NIPS’12. USA: Curran Associates Inc., 2012, pp. 1097–
1105.

k-近邻搜索
[40] J. L. Bentley, “Multidimensional binary search trees used
for associative searching,” Commun. ACM, vol. 18, no. 9,
pp. 509–517, Sep. 1975.


## 引言
射电频率干扰是射电望远镜采集到的来自于人类活动或者自然界的非天文信号。射电频率干扰普遍的存在于射电天文观测中，而近几十年来，随着人类对于射电波段开发的快速发展，射电望远镜在接收到目标科学信号的同时也接收到了大量的射电频率干扰。[flag]来自诸如地面设备、移动通讯、人造卫星等射电信号发射源的干扰，在许多射电望远镜的工作频段内都存在着强烈的干扰信号，甚至普遍的高于目标射电天文信号[flag]。

射电频率干扰对于射电天文科研工作的影响很大，一方面，强烈的射电频率干扰降低了射电信号的信噪比，使得准确的目标信号变得极其困难[flag]；其次，大部分射电频率干扰的信号仍是未知的，很难采用常规方法获得其在时域以及接收频域上的分布，这也就意味着很难对这些信号进行确切的补偿[flag]；此外，对于特定的目标源例如脉冲星而言，周期性的射电干扰会对其造成极大程度上的影响，不仅可能导致判断出错误的脉冲星候选体，也可能导致在脉冲星周期的拟合和判断上出现失误[flag]。

为了极大程度的降低这些射电干扰的影响，大型射电望远镜在进行选址和建设的过程中，往往会进行电磁环境的严格筛查，并且设置射电静默区，同时加装一系列射电屏蔽装置，以及采用其他阻止射电频率干扰进入射电望远镜接收装置的措施[flag]。尽管如此，能够进入射电望远镜的干扰信号依旧很多很杂[flag]，如何有效的消除这些干扰信号，进而进行更加深入的射电天文研究，是射电天文数据处理中一大挑战。

500米口径球面射电望远镜（Five-hundred-meter Aperture Spherical radio Telescope，以下简称FAST）[flag]是目前世界上最大单口径、最灵敏的射电望远镜，于2016年9月建成并投入测试[flag]，于2017年10月首次发现新脉冲星[flag]。由于FAST自身的超高分辨率，在接收到来自遥远宇宙中的天体信号的同时，也接受了大量来自地面和人造卫星的电磁干扰信号。这些干扰信号对于FAST的数据分析和科学目标探测造成了很大的影响，因此，降低这些干扰信号的影响，成为尚年轻的FAST亟待解决的重要问题之一。

在以往的研究中，科学家们提出了大量的算法来去除射电信号中的嘈杂干扰，其中包括：

…………

上述的种种方法往往采用各种技术来尝试检测和去除射电信号中干扰信号，而最近FAST开始尝试从分离出来射电频率干扰信号的特征出发，寻找这些信号的可能来源。[flag:Yuan, Mao]他们首先将来自FAST超宽带接收器的射电信号以接收频率通道作为维度进行主成分分析，提取出主要的干扰信号成分；接着提出了一个分类程序，将射电频率干扰在频域上氛围窄带类型和宽带类型，在时域上分成了三种主要的类别：脉冲型，周期型以及随机型。其中脉冲型的射电干扰是一个或者一些强烈的短脉冲；周期型的射电干扰是具有明显周期型的，可重复的信号；随机型指的是没有明显的脉冲或者周期特征，呈现出较长期波动的信号。最后，讲这些分类之后的信号记录在目录之中，以便对其进行进一步的统计分析。

本文试图在上述论文描述的方法上更进一步。首先，主成分分析算法是一个经典的统计学方法，不仅能够应用于时域信号的分离，也能够应用于谱线的分离，所以，我们尝试着在频谱上进行主成分分析，从另一个角度尝试获取不同的分离方式和分离结果；其次，在上述三种时域分类中，周期型的干扰信号对于科学目标的影响最为关键，同时对于强周期性的信号而言，其具有着明显的频谱特征，因此我们着重于窄带周期性信号的分析与研究。第二节将介绍将上述方法应用于FAST19波束接收器之后的结果和分析，第三节将介绍对原始数据转换到频域空间进行双重滤波之后再利用主成分分析进行分离的结果以及分析，在第四节中则讨论了一些其他可能进行的方法以及这些方法的制约之处，同时对未来的工作方向提出一些设想。

## 时域信号的主成分分析

首先，我们对19波束接收机接受到的约260s的信号直接进行了主成分分析，得到的结果如图
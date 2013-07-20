---
layout: post
title: Actuary-in-box
author: 孙丹丹
categories:
- result
---   

---

欧盟偿付能力框架(Solvency II)下的最重要的准则之一，就是它选择的时间的跨度是一年，而不是最终。所以，在做Solvency II下的准备金时，尽管应用的是随机准备金技术，但是并不是大家通常理解下的随机准备金结果。在欧洲的精算圈子称为“Actuary-in-the-Box”，直译为“盒子中的精算师”。我们要想理解“Actuary-in-the-Box”，那么我们就必须要知道在计算准备金时Solvency II下的原则与传统的原则的区别是什么。

###一、一年期原则与传统的最终原则主要的差异

传统观点下，准备金风险是指提留的准备金与未来所有赔付（直到赔付全部结束) 的差距，而Solvency II下的一年期是指提留的准备金与下一个赔付年度结束时产生的增量赔付与再次提留的准备金加总的差距。
在计算风险边际时，一年期原则与传统的最终原则关键的差异在于对偿付能力的资本要求SCR(t)的理解和计算上。下面用一个例子来说明他们之间的差异。

事故年2011在2011.12.31时点的赔款金额是100元，它在2012进展年和2013进展年的增量赔款金额分别是X元和Y元，2013年后进展完毕，再也没有赔款金额了。

在Solvency II下，SCR(2011年底)仅仅是保障2012年出现的赔款金额（X）的不确定性，确保2012年底资产负债表的95%安全性，它并不考虑将在2013年出现的赔款金额（Y）的不确定性，2013年出现的赔款金额（Y）的不确定性是要由2012年底时评估的SCR（2012.12.31）去考虑的问题。这就是Solvency II的一年期原则，也说明了一年原则和最终原则的本质区别。

###二、“Actuary - in -the -Box ”的含义

1、对各个事故年度在 2007 年度的进展赔付进行模拟，将模拟得到的赔付添加到原来的流量三角形中，构成一个新的流量三角形, 并将模拟得到的增量赔付之和记为 $C^{1}_{k}$ 。

![](http://reserverisk.github.com/images/2.png)

2、在新的赔款流量三角形基础上，按照准备金评估模型计算此时的未决赔款准备金，记为$R_{k}^{1}$ 。

3、按照公式     $$CDR_{k} =R^{0} -C_{k}^{1} -R_{k}^{1}$$           (会计年度k)计算得到赔付进展结果的一次模拟值。从 1 到 3 可以看做把赔款流量三角形打开（模拟赔付）并关闭（计算准备金$R_{k}^{1}$ ）的过程，就像是在一个盒子里进行的运算一样，我们把这个过程又称为“actuary-in-box”。
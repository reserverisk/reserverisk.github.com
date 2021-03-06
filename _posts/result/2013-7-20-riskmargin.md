---
layout: post
title: 风险边际（Risk Margin)
author: 田静
categories:
- result
---   

---

###一、风险边际的含义

什么是风险边际？风险边际是在保险精算界和金融投资界常用的一个概念，在不同的领域有着不同的定义。在保险精算中，风险边际一般被定义为代表着实际结果与最佳估计值相比的偏差风险的一个数值，象征了风险度量的大小。所谓保险负债的风险边际,是指保险公司为应对未来支出现金流在金额和时间上超过预期而产生的不确定性,需计提超出负债平均值的额外负债。
Solvency II中反对含糊的所谓“保守估计”，而是要求必须给出“最佳估计”并明示“风险边际”，当然，你可以认为，“最佳估价”加上“风险边际”就是以前常说的“保守估计”。可以说风险边际在Solvency II里的具体环境中就是指最佳估计负债值之上的一个储备负债值。

风险边际的目的是传达了一种关于未来现金流不确定性的指示信息。如果实际支付没有达到预估的水平,风险边际就会对利润产生积极的影响;如果实际支付超出预期,风险边际就会减少不利经验对于利润的消极影响,因此,风险边际通常起到平滑利润波动的作用,但是它不能用来为巨灾和大损失提供平滑作用。

###二、风险边际的计算方法

目前,保监会规定,对于非寿险业务,可以根据自身数据测算确定风险边际,但方法限定为75%分位数法和资本成本法。

####1.分位数法

（1）概念与方法

欧II量化影响研究2（QIS2）中提出可以用分位数法计量风险边际，

$$ 风险边际=max\{L_{75\%}-BEL，0.5 \times \sigma_{L}\} $$

上式中，L 表示负债，$$ L_{75\% } $$ 表示负债的75%分位数，BEL表示负债的最优估计，$$\sigma_{L}$$ 表示负债的标准差。负债的最优估计，是评估时点负债现金流的期望值，所谓最优，一是确定未来现金流要根据评估时点的所有信息，二是以最优折现率对现金流折现。

这种方法的思路是在假设负债分布的条件下，先确定其75%的分位数，它与最优估计负债之间的差值即为风险边际，再考虑到可能会有极端的厚尾分布（strong skewed distribution），因此将风险边际确定为75%分位数与0.5倍标准差的较大值。

（2）计量的优缺点

分位数法通常用于分析保险公司单一产品线的理赔数据，计量非寿险准备金风险边际时效果明显，但也存在以下缺点：

- 分位数法不考虑市场一致性问题；
- 需要假设负债的分布，分布偏斜度对风险边际的计量有重大影响；
- 寿险产品风险多样，负债现金流分布不易确定，很难准确估计分位数。

####2.	资本成本法（CoC，Cost of Capital）

（1）概念

资本成本法的基本思想是：从市场的角度看，任何使用资本进行交易的行为必然产生成本，保险公司交易的是风险，即产生大量的保险合同负债，负债需要占用资本，从而产生成本，因此这种成本应当看作额外的负债，称之为风险边际，一并计入负债。这种方法称为资本成本法，资本成本法以保险业务的市场价格为基础计提准备金，以保证在保险公司转移业务或者被兼并时仍对有效期内的保单具备偿付能力。

（2）计量方法

$$ 风险边际= \sum^{T}_{t=0}\frac{SCR(t)\times CoC}{(1+r_{f})^t} $$

其中t=0 代表评估时点;T表示保险业务的责任年限；$$r_{f}$$ 表示无风险利率；SCR（t）（Solvency Capital Requirement）表示保险公司t时刻的偿付资本要求；CoC 即资本成本率，反映公司的筹资成本。SCR（t）×CoC 反映了负债风险占用资本的成本，SCR（t）每年必须重新计算。CoC 根据保险公司融资成本确定，融资成本则由外部评级机构的评价确定。由于SCR 必须保证在所有情境下都能满足保险公司的偿付要求，因此CoC是长期的稳定阶段和不利阶段下的平均资本成本率，欧II中将之确定为6%,这是欧洲信用评级为BBB 公司的融资成本。确定保险公司t时刻的偿付资本要求是资本成本法计量风险边际的难点和重点。

（3）资本成本法的优缺点

- 与国际财务报告准则的发展更为一致；
- 计量风险边际比较直接和透明，而且更容易被理解和使用；
- 资本成本法是协商转移人寿保险业务时的基础，代表了市场一致定价的一种形式；
- 风险边际高度依赖于设定的资本成本率，而在实际中不同公司甚至不同产品的资本成本率不尽相同；
- 偿付能力资本的计量极其复杂，使用成本高。

(4)运用资本成本法计算风险边际的例子

假设某直保公司ABC在2009年12月31日,对企业财产保险业务组合的未决赔款准备金(UPR)为40亿元(假定它是合理的最佳估计值),什么是退出价格呢?简单地说,也就是假设ABC计划在2010年退出企业财产保险市场,因此希望将2009年底的企业财产保险业务的未决赔款准备金全部通过再保险合同移给DEF公司,那么ABC公司应该给DEF公司多少钱才能使DEF公司愿意接受这笔保险业务呢?这就是这笔保险业务的当前市场价格,退出价格就是指该业务的市场价格。又如何求风险边际呢?

首先，接受这笔业务组合，肯定是需要一笔资本金支持的。至于这个资本金如何去度量，还是一个存在争议的为题。目前国际上比较流行的资本金度量有3个观点：一是用法定的偿付能力资本（比如美国的RBC或者欧盟的Solvency II），二是使用经济资本（Economic Capital）模型计算出的经济资本，三是使用公司自有资本金按照一定的分配算法计算得到的分配资本金。

为了简化问题,我们假设监管机构要求的资本金为自留保费额的1/4,这样DEF公司接受这笔40亿元业务后,需要偿付能力资本金是10亿元。资本成本是被占用的资本金如果按照同等风险程度做投资后可以得到的机会成本 ,如果同风险的投资回报率为7.8%。

首年的资本成本为:10×7.8%=0.78亿元;

首年的资本成本确定后,要确定未来年的资本成本,假定在2010年底未决赔款准备金为24亿元,2011年底的未决赔款准备金为8亿元,无风险利率为3%

2010年的资本成本为:24×1/4×7.8%=0.468亿元;

2011年的资本成本为:8×1/4×7.8%=0.156亿元
     
当然，这样计算出来的风险边际是可以通过推向市场去验证的，比如ABC大胆地尝试真实地将这笔财产保险业务转移给市场上的公司，如果按照41.381亿元作为转让价格依然没有公司解盘，那么这个风险边际显然低估了真实的“退出价值”。

---









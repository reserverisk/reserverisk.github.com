---
layout: post
title: "R笔记"
description: ""
category: ramblings
tags: [ramblings, startups]
categories:
- rlang
- topic
show_img: "/images/LearnR_2.png.png"
---



---

1.pretty.划分等间隔。axis,对坐标轴进行更改。mtext坐标轴标签。mar参数使用。
    

	library(MASS)
	data(wtloss)
	oldpar <- par(mar = c(5.1, 4.1, 4.1, 4.1))
	attach(wtloss)
	plot(Days, Weight, type = "p")
	Wt.lbs <- pretty(Weight*2.205)
	axis(side = 4, at = Wt.lbs / 2.205, lab = Wt.lbs)
	mtext("Wt.lbs", side = 4, line = 3)#line可调节标签与坐标轴距离
	detach(wtloss)

![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_1.png)


---

2.[如何保存数据](http://cos.name/cn/topic/106512#post-230001)，[如何读取数据，https：读取数据的一些设置问题。](http://cos.name/cn/topic/108840?replies=9#post-240472)

---

3.透明颜色，以避免重叠<code>rgb(x,y,z,alpha)</code>


	x <- 1:100
	y <- rnorm(100, 0, 5) + 2 * x ^ 0.5
	plot(x, y)
	for (i in 1:50) {
	ind <- sample(1:100, 100, replace = T)
	lines(lowess(x[ind], y[ind]), col = rgb(0, 0, 0, 0.05))
	}

![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_2.png)
    
---

4.lattice 中的三维图

	x <- seq(0, 2, 0.1)
	y <- seq(0, 2, 0.1)
	xy <- expand.grid(x = x, y =y  )
	data.grid <- cbind(xy, z = xy$x^0.5 + xy$y^0.5)
	library(lattice)
	trellis.device()
	wireframe(z ~ x + y, data.grid, 
			drape = T, screen = list(z = 20, x = - 50))

![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/lattice3d.png)

---

5.[太极图代码](https://gist.github.com/1b36e494d614e2b6defa)，关键看如何消去所有主题元素，ggplot相关


	data <- cbind(data1, data2, data3, data4)
	p <- ggplot(data, aes(x = x, y = y))
	p + geom_polygon(fill = "white", colour = "black")  + geom_polygon(aes(x=x2, y=y2), fill = "black") + 
	geom_polygon(aes(x=x3, y = y3), fill = "white") +
	geom_polygon(aes(x=x4, y = y4), fill = "black") + 
	opts(axis.title.x = theme_blank(), axis.title.y = theme_blank(), 
		panel.background = theme_blank(), axis.text.x = theme_blank(), 
		axis.text.y = theme_blank(), axis.ticks = theme_blank(), 
		panel.grid.minor = theme_blank())



![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_3.png)

---

6.坐标轴。标度重画，箱。


	re <- listre$r[listre$k==4, ]
	par(las = 1) # 标度总是水平
	plot(log(apply(re,2, mean)), type = "l", ylim = c(-4, -1.5), lty = 3, ylab = "",
	xlab = "", axes = F)
	axis(1, at = 1:10, labels = 0:9)
	axis(2)
	box()
	lines(log(apply(re,2, mean) + 2 * apply(listre$r, 2, sd)), lty = 3)
	lines(log(apply(re,2, mean) - 2 * apply(listre$r, 2, sd)), lty = 3)
	lines(log(r), lty = 4)
	points(log(r), pch = 5)
	alpha <- -1.6159
	beta <- 0.2
	r.true <- NULL
	r.true[1:4] <- c(15.9, 17.9, 17.9, 13.9) / 100
	r.true[5:10] <- exp(alpha - beta * (4:I))
	lines(log(r.true))
	points(1:10, log(apply(re,2, mean) + 2 * apply(listre$r, 2, sd)),
	pch = 4, cex = 0.5)
	points(1:10, log(apply(re,2, mean) - 2 * apply(listre$r, 2, sd)),
	pch = 4, cex = 0.5)
	abline(h = seq(-6, -1, length = 6), col = rgb(0, 0, 0, 0.1))
	legend(5.5, -1.5, legend = c("数据设计参数", "RJMCMC结果", "MLE结果", "RJMCMC上下两个标准差区间"),
	pch = c(-1, -1, 5, 4), lty = c(1, 3, 4, 3), bty = "n")
	text(1, -1.5, labels = "log(r)")
	text(9.8, -4, labels = "进展年")
	#abline(v = 1:10, col = rgb(0, 0, 0, 0.1))


![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_4.png)

---

7.Everything in R is an object;Every object in R has a class.
1.  vector's various type:
    1.  charcter
    2.  "numeric"
    3.  "logical"
    4.  "integer"
    5.  "complex"
    6.  "list"(?)


---

8.<code> save.image()</code> 可以在R会话过程中，保存工作空间。

---

9.<code> unclass() </code>一方面复制对象，另一方面返回对象的属性。


	> a <- 5
	> attr(a, "t") <- "gaolei"
	> unclass(a)
	[1] 5
	attr(,"t")
	[1] "gaolei"


---

10.ASK: Why might we want to use "Factor"? Reply:Using a factor indicates to many statistical function that it is a categorical variable, so it is treated specially.

---

11.<code>par(pty = "s")</code>做出的图总是正方形的，无需再调。

![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_5.png)

---

12.关于R的作图。一个感觉就是，拿到数据，不是不知道该如何作图，而是不知道该用哪些图来表现数据。除了pie,bar，hist,line，其他就不知该用什么图了。超哥今天下午和我一起做了几张图，用来表现几种数据，觉得获益匪浅。

- 关联图。用来表示列联表数据，尤其是反应两个交叉因素是否独立。

例子1：
<pre><code>
> data <- rbind(c(41,111,13), c(97,105,5))
> data <- as.table(data)
> dimnames(data)[[1]] <- c("去过", "没去过")
> dimnames(data)[[2]] <- c("没有", "有，但不多", "有很多")
> assocplot(data, xlab = "是否考虑过去养老机构生活", ylab = "周围有没有人去养老机构养老")
> box()
</code></pre>
![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_6.png)

如果每个单元格脱离基线比较远，则说明两因素并不独立。

例子2：
<pre><code>
> data <- rbind(c(9, 38, 16, 1), c(0, 5, 1, 0),
+ c(0, 1, 0, 0), c(0, 1, 0, 1))
> data <- as.table(data)
> dimnames(data)[[2]] <- c("非常好", "基本良好", "不太好", "极其不好")
> dimnames(data)[[1]] <- c(1, 2, 3, 4)
> assocplot(data, xlab = "调查对象对居家养老的排序", ylab = "身体状况")
> box()
</code></pre>
![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_7.png)

---
- 一维数据的随机展示。

例子：
<pre><code>
bed <- c(712, 516, 750, 970, 100, 50, 439, 12000, 838, 2277, 66)
plot(1:11, rnorm(11, 4, 1),ylim = c(-1, 8), type = "p", pch =16, cex = c(2,2,2,2,1,1,1,3,2,3,1),
 col = c(rep(2, 8), 3, 4, 4), xlab = "", ylab = "", axes = F)
box()
legend(9, 8, legend = c("北京", "上海", "天津"), col = c(2, 3, 4), pch = 16, cex = 0.7 )
</code></pre>
![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_8.png)

注意其中使用到的y数据其实随机的，用圈的大小（cex)表示了数据的相对大小，这样比简单的bar就直观舒服些。另外，并不是严格按照源数据，而是进行了分级转换。还有，图例的大小也是可以控制的(cex).

---
- 多维数据的展示。脸型图。脸型图中最为传神的是眼眉的弯曲，以及嘴的弧度。在瞌睡的场合，脸谱图有提神的功效。
<pre><code>
library(TeachingDemos)
data <- rbind(c(80394, 32903, 13.2), 
    c(82560, 36230, 13.8), 
    c(85213, 26921, 10.8))
faces2(data, which = c(3, 14, 12), labels = c("北京", "上海", "天津"), ncols = 3)
</code></pre>
![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_9.png)

其中一个重要参数就是which,用来指定每列数对应于什么位置，鼻子还是眼睛，或脸的大小。

1. 额头和脸之间的横线宽度（一张脸谱上半部分为额头，下半部分为脸）
2. 额头和脸的相对高度（取值越大则额头越矮脸越高）
3. 脸高
4. 上半边脸的宽度
5. 下半边脸的宽度
6. 鼻子长度
7. 嘴巴高度
8. 嘴巴弧度（绝对值应小于9）
9. 嘴巴宽度
10. 眼睛高度
11. 两只眼睛之间的距离（取值0.5~0.9）
12. 眼睛和眉毛的弧度
13. 眼睛圆圈的形状（取值越大越呈椭圆形，越小越圆）
14. 眼睛大小
15. 眼珠和眉毛的位置（越大越靠左，越小越靠右）
16. 眉毛高度
17. 眉毛弧度
18. 眉毛宽度

---
- 金字塔类图的画法，尤其是那种组成比例的那种。不过还没找到，成型的函数。只能用矩形来堆积了。
<pre><code>
> plot(1, 2, type = "n", xlim = c(0, 100), ylim = c(1.5, 5.5), axes = F, xlab = "北京", 
+   ylab = "" )
> rect(50-4.3, 2, 50+4.3, 3, col="green")
> rect(50-41.35, 3, 50+41.35, 4, col="red")
> rect(50-4.35, 4, 50+4.35, 5, col="yellow")
> abline(v = 50)
</code></pre>
![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/LearnR_10.png)

---

13.坐标图做法。多边形、公式。
<pre><code>
plot(1:10, type = "n", axes= F,  xlim = c(-1, 12), ylim = c(-1, 13), xlab = "", ylab = "")
arrows(-1,0,10,0)
arrows(0, -1, 0, 13.5)
abline(3, 2)
x <- c(0, 0, 4.5)
y <- c(3, 12, 12)
text(-1, 10, "M")
text(5, -1, "T")
polygon(x,y, col = "orange")
text(6, 10, expression(M == u + (1+theta)*lambda*T))
</code></pre>

![dubian](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/jingsuan2.png)

---

14.顿时亮了, 干净整洁的数据表达形式。
<pre><code>
\begin{frame}[fragile]
\frametitle{关于数据的设计}
<<echo=FALSE,comment="",size = "tiny">>=
options(width = 100)
library(LearnBayes)
X <- read.table("data.txt")
names(X) <- 0:9
rownames(X) <- 0:9
X
alpha <- -1.6159
@
\end{frame}
</code></pre>
配图：

![dubian](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/knitr1.png)

---

15.改变工作目录。

<pre><code>
setwd("e:\github\")
</code></pre>

---
16.Rnw插入图片,调整大小的关键参数out.width.面对庞大数据，最好采用加载的方法，而不是直接运行。数据保存可以用save(x1, x2, ..., file = "data1.RData")：
<pre><code>

<<fig.width=4, fig.height=4,  out.width='0.46\\linewidth', echo=FALSE, cache=TRUE>>=
load("E:/data1.RData")
hist(apply(C.result, 1, sum), xlab = "", ylab = "", main = "", freq = F)
lines(density(apply(C.result, 1, sum)), col = 2)
@
</code></pre>

![dubian](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/rnw.png)

隐藏结果的参数为results="hide".

---

17.关于mar,oma的设置，注意单独在par()里设置，不要混在plot()里。
[参见这里](http://research.stowers-institute.org/efg/R/Graphics/Basics/mar-oma/index.htm).

---
18.圆形区域

<pre><code>
par(mar = rep(0, 4))
par(mai = rep(0, 4))
plot(-6:6, type = "n", axes= F,  xlim = c(-6, 6), ylim = c(-6, 6), xlab = "", ylab = "")
arrows(-5,0,5,0)
arrows(0, -5, 0, 5)
theta <- seq(0, 2*pi, length = 100)
segments(0,0, 2^1.5, 2^1.5, col = 2, lwd = 2)
text(2, 2, expression(R[0]))
polygon( 4 * cos(theta),  4*sin(theta),density = 10, angle=-15, border = NA)
</code></pre>

![LearnR](https://github.com/gaolei786/gaolei786.github.com/raw/master/images/boxmuller2.png)

---
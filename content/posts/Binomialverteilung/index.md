---
title: 二项分布令人迷惑的n次和1次实验的期望
date: '2016-02-14T16:54:47+01:00'
categories:
- 求学德国
tags:
- 二项分布 Binomialverteilung
description: 缘自不理解二项分布的期望，方差和似然函数，而又必须面对期末考试，为了不挂科所以必须把这些概念和推导搞明白。
---

缘自不理解二项分布的期望，方差和似然函数，而又必须面对期末考试，为了不挂科所以必须把这些概念和推导搞明白。

### 二项分布是啥？

伯努力实验（Bernoulli-Experiment）：非黑即白，只有{1,0}两个结果。1:事件发生，0:事件不发生。  
一般我们会做这样的实验：抛n次硬币，m次是头(Kopf)的概率。这就服从二项分布。

**特别注意：**我们必须分清，整个N次实验对应的随机变量X和单次的（比如：$\bar X$，此时$\bar X$对应的正态分布函数和X是不同的。）

---

### N次和1次

首先我必须吐槽一下，我个人经常被二项分布里的N次实验和1次实验（比如均值）给弄得找不着北。我们知道期望一般都是用符号$\mu$来表示，但是经常我们看到的是这样：

- $N次实验: E(X)=\mu$
- $均值\bar X的期望: E(\bar X)=\frac{1}{n}\sum_{i=1}^nE(x_i)=\frac{1}{n}n\mu=\mu$

我不禁要说，这是闹哪样？你俩的结果看起来完全一样！这导致我一直不理解二项分布。实际上我们应该像[wikipedia](https://zh.wikipedia.org/wiki/%E4%BA%8C%E9%A0%85%E5%88%86%E4%BD%88)上一样写：

- $N次实验: E(X)=\mu_n$

  下标加上n就知道是n次伯努力实验，因此$\mu_n=np$。
- $均值\bar X的期望: E(\bar X)=\frac{1}{n}\sum_{i=1}^nE(x_i)=\frac{1}{n}n\mu=\mu$

  这里不用变，因为就表示一次伯努力实验，一次实验的结果只有0和1的可能。当P代表出现的概率时，$E(x_i)=P+0(1-P)=P=\mu$。所以一次实验的期望始终是P。

### 二项分布均值的期望和方差

事件发生的概率 P，对应于值「1」  
事件未发生的概率 1-P，对应于值「0」

1. 一次伯努力实验的期望和方差，如下：  
$E(x_i)=P+0(1-P)=P=\mu,i=1,2,3…n$  
$Var(x_i)=E((x_i-\mu)^2)=E(x_i^2)-\mu^2=1^2P+0^2(1-P)=P-\mu^2=P-P^2=P(1-P)$
2. 均值的期望和方差  
$E(\bar X)=\frac{1}{n}\sum_{i=1}^nE(x_i)=\frac{1}{n}n\mu=\mu＝P$  
$Var(\bar X)=Var(\frac{x_1+…+x_n}{n})=\frac{1}{n^2}\sum_{i=1}^nVar(x_i)=\frac{1}{n^2}n\sigma^2=\frac{\sigma^2}{n}=\frac{P(1-P)}{n}$

### 正态分布关于均值的考试题型

我经常在置信区间遇到这种类型的题目。比如平时练习中的一道题：

> Ein Psychologe misst bei 100 zufällig ausgewählten Personen die Reaktionszeit auf ein bestimmtes Signal. Dabei ergibt sich ein Mittelwert von $\bar X = 0,80$ Sekunden. Unter Annahme, dass die Zufallsvariablen $X_1, …, X_{100}$, welche die Reaktionszeit beschreiben, unabhängig und $N(\mu, 0,04)$-verteilt sind, berechne man ein 0,95-Konfidenzintervall für $\mu$.  
> 一次心理测验中，随机选中100个人，测试其对于一个特定信号的反应时间。给定平均值为0,80秒。在这种假设下，每个随机变量$X_1, …, X_{100}$都描述反应时间，它们互相独立且满足$N(\mu, 0,04)$正态分布，求0,95-置信区间下的$\mu$。注：0,04=0.04

给定如下正态分布表格

| $\alpha$ | 0,05 | 0,025 | 0,005 | 0,0025 |
| --- | :---: | :---: | :---: | :---: |
| $1-\alpha$ | 0,95 | 0,975 | 0,995 | 0,9975 |
| $\phi^-1(1-\alpha)$ | 1,645 | 1,960 | 2,576 | 2,807 |

解:  
标准化均值随机变量：$\frac{\bar X-E(\bar X)}{\sqrt{Var(\bar X)}}=\frac{\bar X-\mu}{\sqrt{\frac{\sigma^2}{n}}}=\sqrt{n}\frac{\bar X-\mu}{\sigma}$

$\alpha=0,05 \Leftrightarrow 1-\frac{\alpha}{2}=0,975$  
查表可知：$c=\phi^{-1}(0,975)=1,960$

又$P(|\sqrt{n}\frac{\bar X-\mu}{\sigma}|\leq c)=1-\alpha=0,95$

$|\sqrt{n}\frac{\bar X-\mu}{\sigma}|\leq c$  
$\Leftrightarrow -c \leq\sqrt{n}\frac{\bar X-\mu}{\sigma} \leq c$  
$\Leftrightarrow -c\frac{\sigma}{\sqrt{n}} \leq \bar X-\mu \leq c\frac{\sigma}{\sqrt{n}}$  
$\Leftrightarrow -c\frac{\sigma}{\sqrt{n}}-\bar X \leq -\mu \leq c\frac{\sigma}{\sqrt{n}}-\bar X$  
$\Leftrightarrow c\frac{\sigma}{\sqrt{n}}+\bar X \geq \mu \geq -c\frac{\sigma}{\sqrt{n}}+\bar X$  
将$\sigma=\sqrt{0,04}=0,2, n=100, \bar X=0,8, c=1,96$代入上式得：  
$1,96\frac{0,2}{\sqrt{100}}+0,8 \geq \mu \geq -1,96\frac{0,2}{\sqrt{100}}+0,8$  
$\Leftrightarrow 0,8392 \geq \mu \geq 0,7608$

因此$\mu \in [0,7608 , 0,8392]$是$\mu$的0,95-置信空间。  
也就是说我们估计$\mu$有95的概率落在[0,7608 , 0,8392]此区间。

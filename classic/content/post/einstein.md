---
title: Bedload diffusion theory due to Einstein
author: JKP
date: '2019-07-05'
categories:
  - bedload transport
  - stochastic modeling
tags:
  - Science
---

Hans Albert Einstein was a civil engineer and the son of Albert Einstein, the famous physicist.
In his PhD work before 1937, he performed a series of experiments tracking painted sediment through a model river [1].
His goal was to develop the ability to predict sediment transport in real rivers.

Einstein recognized that individual grains within the stream moved in an alternating sequence of motion and rest periods, and he attempted to characterize the distance of individual motions and the duration of individual rests.
During his experiments, he realized these characteristics were not predictable, so he considered them as statistical quantities, eventually characterizing the step length and resting time by exponential distributions:
$$ \psi_1(t) = k_1 e^{-k_1 t}$$
$$ \psi_2(r) = k_2 e^{-k_2 r}$$
In these equations, $1/k_1$ represents the mean rest period, and $1/k_2$ represents the mean step length.

Einstein eventually computed the probability density $P(x,t)$ to find a grain at position $x$ at after time $t$, provided it started at position $0$ at time $0$, provided it moves in relatively instantaneous and exponentially distributed steps interrupted by exponentially distributed rests.
Modern stochastic physics approaches provide an efficient derivation of Einstein's result.
In the spirit of physical random walks [2,3] or renewal theory [4], we can write $P(x,t)$ as a convolution integral over all previous positions:
$$ P(x,t) =  \int dx' \int dt' p(t-t')q(x-x')P(x-x',t-t')$$

1. Einstein 1937
2. Montroll and Weiss, 1964
3. Weiss 1994 
4. Cox 1964




---
title: Einstein's bedload diffusion theory
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
His was to understand sediment transport in real rivers.

Einstein recognized that individual grains within the stream move in an alternating sequence of motion and rest periods, and he attempted to characterize the distance of individual motions and the duration of individual rests.
During his experiments, he realized these characteristics were not predictable, so he considered them to be statistical quantities, eventually characterizing the step length and resting time with exponential distributions:
$$ \psi_1(t) = k_1 e^{-k_1 t} $$
$$ \psi_2( r) = k_2 e^{-k_2 r}$$
In these equations, \\(1/k_1\\) represents the mean rest period, and \\(1/k_2\\) represents the mean step length.
A typical trajectory of a grain moving downstream can be modelled like this, according to Einstein:

!["Einstein Trajectory"](/ein1.png)

Armed with this stochastic concept of bedload motion, Einstein set out to compute the probability density \\(p(r,t)\\) to find a grain at position \\(r\\) at after time \\(t\\), provided it started at \\(r=0\\) and \\(t=0\\).
Einstein's original derivation is clear, but it appears somewhat clumsy from the standpoint of contemporary stochastic physics.
In the spirit of physical random walks [2,3], we can write \\(P(r,t)\\) more efficiently as a convolution integral over all previous positions:
$$ p(r,t) =  \delta( r)e^{-k_1 t} + \int_0^r dr^\prime \int_0^t dt^\prime \psi_1(t^\prime)\psi_2(r^\prime)p(r-r^\prime,t-t^\prime).$$
The first term in this equation represents the possibility that a grain has never moved from its initial position by the time \\(t\\), while the second term represents the possibility that a grain arrived at the position \\(r\\) after a step of length \\(r^\prime\\) and a rest of time \\(t^\prime\\).

To solve this integral equation for \\(p(r,t)\\), we can use the Laplace transform method, mapping the problem to an alternate space in which the convolution structure is unravelled.
Using the double Laplace transform \\( \tilde{p}(\eta,s) = \int_0^\infty dx \int_0^\infty dt e^{-\eta x - s t}p(x,t)\\) in this equation provides 
$$ \tilde{p}(\eta,s) = \frac{1}{s+\frac{k_1\eta}{k_2+\eta}}.$$

There are many ways to solve this equation to arrive at \\(p( r, t)\\).
One that I haven't seen in the literature yet is to multiply both sides by \\( s+\frac{k_1\eta}{k_2+\eta} \\) and invert the Laplace transforms, taking account of the property that division in Laplace space is equivalent to differentiation in the original space.
This provides an asymmetric diffusion equation:
$$[k_1\partial_r + k_2 \partial_t + \partial_r \partial_t ]p( r,t) = 0,$$
which has the solution (obtained by the Frobenius method)
$$ p( r,t ) = e^{-k_1 t -k_2 r}[ \sqrt{\frac{k_1 k_2 t}{ r}} I_1( 2\sqrt{k_1k_2 r t}) + \delta( r) ] , $$
identical to Einstein's original result [1]. 

Recently, I used this approach, which is more closely rooted in contemporary stochastic physics methods than Einstein's original approach, to generalize his theory to include the possibility that sediment can become buried within the sedimentary bed for relatively long periods during the course of its downstream transport.
Ultimately, I derived three stages of bedload diffusion, where the rate at which tagged grains spread apart can have three distinct values depending on the timescale of observation.
This work is submitted to Geophysical Research Letters and I should hear back from the peer review soon.

## References
1. Einstein, H. (1937). Der Geschiebebetrieb als Wahrscheinlichkeitsproblem, Verlag Rascher, Zurich (Engl. trans.: in: Shen, H. (Ed.), 1972. Sedimentation. Symp. to Honor H.A. Einstein. H.W. Shen, Fort Collins, CO).

2. Montroll, E.W., & Weiss, G.H. (1965). Random Walks on Lattices. II. _Journal of Mathematical Physics_, 6, 167-181.

3. Weiss, G.H. (1994). _Aspects and Applications of the Random Walk_. Amsterdam; North Holland.

4. Cox, D., & Miller, H. (1965). _The Theory of Stochastic Processes_. London; Chapman and Hall.




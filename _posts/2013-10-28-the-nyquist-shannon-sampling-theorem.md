---
layout: post
title: "The Nyquist Shannon Sampling Theorem"
categories:
- 
tags:[Math]
- 


---
The Nyquist-Shannon sampling theorem, after Harry Nyquist and Claude Shannon, in the literature more commonly referred to as the Nyquist sampling theorem or simply as the sampling theorem, is a fundamental result in the field of information theory, in particular telecommunications and signal processing.Sampling is the process of converting a signal (for example, a function of continuous time or space) into a numeric sequence (a function of discrete time or space). Shannon's version of the theorem states:

If a function <p>$x(t)$</p> contains no frequencies higher than <p>$B$</p> hertz, it is completely determined by giving its ordinates at a series of points spaced $\frac{1}{2B}$ seconds apart.

Let $x(t)$ denote any continuous-time signal having a continuous Fourier transform:

<p>$$X(j\omega)=\int_{-\infty}^{\infty}x(t)e^{-j \omega t}dt$$</p>

Let

<p>$$x_d(n)=x(nT)  n=\dots,-2,-1,0,1,2,\dots$$</p>

odnates the samples of <p>$x(t)$</p> at uniform interbals of <p>$T$</p> seconds. Then <p>$X(t)$</p> can be exactly reconstructed from its samples <p>$x_d(n)=x(nT)$</p> if <p>$X(j\omega)=0$</p> for all <p>$|\omega|\geq \frac{\pi}{T}$</p>
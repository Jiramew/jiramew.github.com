---
layout: post
title: "The Nyquist Shannon Sampling Theorem"
categories:
- 
tags:
- 


---
The Nyquist-Shannon sampling theorem, after Harry Nyquist and Claude Shannon, in the literature more commonly referred to as the Nyquist sampling theorem or simply as the sampling theorem, is a fundamental result in the field of information theory, in particular telecommunications and signal processing.Sampling is the process of converting a signal (for example, a function of continuous time or space) into a numeric sequence (a function of discrete time or space). Shannon's version of the theorem states:

If a function <p>$x(t)$</p> contains no frequencies higher than <p>$B$</p> hertz, it is completely determined by giving its ordinates at a series of points spaced $\frac{1}{2B}$ seconds apart.

Let $x(t)$ denote any continuous-time signal having a continuous Fourier transform:

$$X(j\omega)=\int_{-\infty}^{\infty}x(t)e^{-j \omega t}dt$$

Let

$$x_d(n)=x(nT) ~,~ n=\dots,-2,-1,0,1,2,\dots$$

odnates the samples of $x(t)$ at uniform interbals of $T$ seconds. Then $X(t)$ can be exactly reconstructed from its samples $x_d(n)=x(nT)$ if $X(j\omega)=0$ for all $|\omega|\geq \frac{\pi}{T}$

###Proof:

From the continuous-time aliasing theorem, we have that the discrete-time spectrum $X_d(e^{j\theta})$ can be written in terms of the continuous-time spectrum $X(j\omega)$ as

$$X_d(e^{j\omega_{d}T})=\frac{1}{T}\sum_{-\infty}^{\infty}X[j(\omega_d+m\Omega_s)]$$

where $\omega_d\in (-\pi/T,\pi/T)$ is the "digital frequency" variable. If $X(j\omega)=0$ for all $|\omega|\geq \Omega_s/2$, then the above  infinite sum reduces to one term, the $m = 0$ term, and we have

$$X_d(e^{j\omega_{d}T})=\frac{1}{T}X(j\omega_d) ~,~ \omega_d\in (-\frac{\pi}{T},\frac{\pi}{T})$$

At this point, we can see that the spectrum of the sampled signal $X(nT)$ coincides with the nonzero spectrum of the continuous{-}time signal $x(t)$. In other words, the $DTFT$ of $x(nT)$ is equal to the $FT$ of $x(t)$ between plus and minus half the sampling rate, and the $FT$ is zero outside that range. This makes it clear that spectral information is preserved, so it should now be possible to go from the samples back to the continuous waveform without error, which we now pursue.


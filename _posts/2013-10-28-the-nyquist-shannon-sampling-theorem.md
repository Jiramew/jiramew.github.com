---
layout: post
title: "The Nyquist Shannon Sampling Theorem"
categories:
- 
tags:
- 


---

\centerline{\bf \Large The Nyquist-Shannon Sampling Theorem}
\centerline{}
\noindent The Nyquist{-}Shannon sampling theorem, after Harry Nyquist and Claude Shannon, in the literature more commonly referred to as the Nyquist sampling theorem or simply as the sampling theorem, is a fundamental result in the field of information theory, in particular telecommunications and signal processing. Sampling is the process of converting a signal (for example, a function of continuous time or space) into a numeric sequence (a function of discrete time or space). Shannon's version of the theorem states:\\
\indent {\slshape \small {If a function $x(t)$ contains no frequencies higher than $B$ hertz, it is completely determined by giving its ordinates at a series of points spaced $\frac{1}{2B}$ seconds apart.}}\\
\newline{}
Let $x(t)$ denote any continuous-time signal having a continuous Fourier transform:
$$X(j\omega)=\int_{-\infty}^{\infty}x(t)e^{-j \omega t}dt$$
Let
$$x_d(n)=x(nT) ~,~ n=\dots,-2,-1,0,1,2,\dots$$
donates the samples of $x(t)$ at uniform internals of $T$ seconds. Then $X(t)$ can be exactly reconstructed from its samples $x_d(n)=x(nT)$ if $X(j\omega)=0$ for all $|\omega|\geq \frac{\pi}{T}$\\

<p><code>\[
    \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
    1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
    {1+\frac{e^{-8\pi}} {1+\ldots} } } }
    \]</code></p>
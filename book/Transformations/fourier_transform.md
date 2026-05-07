::::{admonition} Attribution
:class: attribution
This page reuses content from {cite:t}`vdBult2025fouriertransform`.
::::


# Fourier transform

(Subsec:Fouriertr:Intro)=

## Introduction

Consider a sound signal. If the sound signal consists of only one tone, then the signal can be moddeled as a single (co)sine. If the signal consists of multiple tones, the corresponding functions are added together. Consider the following incoming signal $f(t)$, as shown in {numref}`Fig:FourierTrs:Introsignal`.

:::{figure} Images/Fig-FourierTrs-Introsignal.png
:name: Fig:FourierTrs:Introsignal

An incoming signal $f(t)$.
:::

[^FootnoteAudio]: The numbers in this function are chosen for mathematical convenience. An audio signal with a frequency of $3$ or $4$ Hz is not audible. In addition, an audio signal does not oscillate around $0$ in practice. 

[^Footnoteplotting]: The graphs look the way we do because $\left|e^{-i\omega t}\right|=1$, so if we just consider $e^{-i\omega t}$ we follow the circle with radius $1$ in the complex plane in clockwise direction. $\omega$ describes how fast we travel through this circle. Since $f$ is real, it only changes the modulus of the complex number $f(t)e^{-i\omega t}$, so we still rotate with the same speed, but the amplitude changes as $f(t)$ changes.

[^Footnotecentermass]: You can imagine this average value by thinking of the curve as a wire with a constant mass density. The average value is then the location of the center of mass of the wire, divided by the length of the time interval (which is $10\pi$ in this case).

[^Footnoteintdomain]: Normally, we integrate from $-\infty$ to $\infty$ (see {prf:ref}`Def:Fouriertr:Fouriertr`), but for this function $f$, the signal is $0$ for $t<0$ and for $t>10\pi$, so this would give the same result.

[^FootnoteFourierseries]: If you are familiar with the Fourier series, you might notice that we could have used this instead of the Fourier transform here. Working with the Fourier series is usually quicker, but it only possible for periodic signals, while the Fourier transform can also be applied for nonperiodic signals.


This signal is the graph of the function $f(t)=\sin(3t)+\sin(4t)$ for $0\leq t\leq 10\pi$, so we are dealing with the sum of a signal with angular frequency $3$ and one with angular frequence $4$.[^FootnoteAudio] However, if we did not know that, how could we find it out? It is rather hard to read this off from the graph directly and you can imagine this gets increasingly harder if more different frequencies are involved. The way to go here is to use the so-called **Fourier transform**[^FootnoteFourierseries].

The idea of this Fourier transform is as follows. We first multiply the signal by the complex exponential $e^{-i\omega t}$. The $\omega$ in this exponential represents an arbitrary frequency, and it can be any positive (or even negative) real number. If we now plot the curve $f(t)e^{-i\omega t}$ with $0\leq t\leq 10\pi$ for various values of $\omega$, we see that usually obtain some pretty curves in the complex plane[^Footnoteplotting]. 

:::::{grid} 2
:gutter: 1
:class-container: full-width

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega1.png
:name: Fig:FourierTrs:omega1

Plot of $f(t)e^{-i\omega t}$ for $\omega=1$. The red dot represents the center of mass of the curve.
:::

::::

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega2.png
:name: Fig:FourierTrs:omega2

Plot of $f(t)e^{-i\omega t}$ for $\omega=2$. The red dot represents the center of mass of the curve.
:::

::::
:::::

:::::{grid} 2
:gutter: 1
:class-container: full-width

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega3.png
:name: Fig:FourierTrs:omega3

Plot of $f(t)e^{-i\omega t}$ for $\omega=3$. The red dot represents the center of mass of the curve.
:::

::::

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega4.png
:name: Fig:FourierTrs:omega4

Plot of $f(t)e^{-i\omega t}$ for $\omega=4$. The red dot represents the center of mass of the curve.
:::

::::
:::::

:::::{grid} 2
:gutter: 1
:class-container: full-width

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega5.png
:name: Fig:FourierTrs:omega5

Plot of $f(t)e^{-i\omega t}$ for $\omega=5$. The red dot represents the center of mass of the curve.
:::

::::

::::{grid-item}

:::{figure} Images/Fig-FourierTrs-omega6.png
:name: Fig:FourierTrs:omega6

Plot of $f(t)e^{-i\omega t}$ for $\omega=6$. The red dot represents the center of mass of the curve.
:::

::::
:::::

It is noticable that the curves for $\omega=3$ and $\omega=4$ look different from the others. Indeed, the other curves are (sort of) symmetric around the origin, while this is not the case for these special values of $\omega$. Of course, these were the two angular frequencies that were present in our signal. 

We can make this a bit concrete. If we integrate the function $e^{-i\omega t}f(t)$ over its domain, we obtain its average value.[^Footnotecentermass] It can be shown that

$$
 \int_{0}^{10\pi}f(t)e^{-i\omega t}\,dt=-\frac{7 (-12 + \omega ^2)  \left(-e^{-10 i \omega  \pi} +1 \right)}{(-16 + \omega^2) (-9 + \omega^2)}.
$$

If we then plot the real and imaginary parts of this expression, see {numref}`Fig:FourierTrs:Fourierintro`, we notice large peaks around $\omega=3$ and $\omega=4$ and also around their negative counterparts $\omega=-3$ and $\omega=-4$. The expression above is known as the **Fourier transform** of the function $f$[^Footnoteintdomain]. This means that we can use the Fourier transform to find out that the original function is built up of a signal with angular frequency $3$ and one with angular frequency $4$. 

:::{figure} Images/Fig-FourierTrs-Fourierintro.png
:name: Fig:FourierTrs:Fourierintro

The real (blue) and imaginary (red) parts of the Fourier transform of the singal $f$.
:::

:::{figure} Images/Fig-FourierTrs-Fourierintromod.png
:name: Fig:FourierTrs:Fourierintromod

The modulus of the Fourier transform of the singal $f$. The modulus appears to be negative for some values of $\omega$, but this is a limitation of the graphing software.
:::


## (Inverse) Fourier transform

Let us formalize the concepts that we have seen in {numref}`Subsec:Fouriertr:Intro`.

::::::{prf:definition}
:label: Def:Fouriertr:Fouriertr
Let $f:\mathbb{R}\rightarrow\mathbb{C}$ be a function for which the improper integral $\displaystyle \int_{-\infty}^\infty |f(t)|\,dt$ converges. Then the **Fourier transform** of $f$ is defined as

$$
 \hat{f}(\omega)=\mathcal{F}(f)(\omega)=\int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt.
$$

When performing a Fourier transform, the domain of the original function is usually reffered to as the **time domain**, while the domain of the Fourier transform of the function is referred to as the **frequency domain** or the **Fourier domain**.
::::::

:::{note}
Although we do allow the function $f$ to take on complex values, we are mainly interested in functions which take on only real values.
:::

The main interpretation here is that $\hat{f}(\omega)$ measures how much of a wave with angular frequency $\omega$ is contained in the signal $f(t)$. For instance, if the signal is light, then, just like a prism, the Fourier transform breaks up the signal into different colours. Or if the signal is sound, the Fourier transform breaks the signal up in the different tones that make up the sound. 

:::{note}
The Fourier transform is also defined for negative values of $\omega$. If $f$ only takes on real values and if $\omega>0$, then we have $\hat{f}(-\omega)=\overline{\hat{f}(\omega)}$. We say that the Fourier transform of a real-valued signal is **conjugate symmetric** (sometimes called **Hermitian symmetric**).
:::

The nice thing about the Fourier transform is that you can also go back to the original function. 

::::::{prf:theorem}
:label: Thm:Fouriertr:InvFouriertr
For a continuous function $f$, for which the Fourier transform exists and for which $\int_{-\infty}^\infty |\hat{f}(\omega)|\,d\omega$ converges, we have 

$$
 f(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}\hat{f}(\omega)e^{it\omega}\,d\omega.
$$

::::::

The proof of {prf:ref}`Thm:Fouriertr:InvFouriertr` is beyond the scope of this book, so we omit this proof. 

There are several generalizations possible of {prf:ref}`Thm:Fouriertr:InvFouriertr`. For instance, it is somtimes possible to take an inverse Fourier transform if the integral $\displaystyle \frac{1}{2\pi}\int_{-\infty}^{\infty}\hat{f}(\omega)e^{it\omega}\,d\omega$ diverges for some values of $t$, or if the function $f$ is not continuous. We will not delve deeper into these generalisations here.

:::{warning}
In some literature, one of the following alternative definitions is used for the Fourier transform

$$\begin{array}{lcllcl}\hat{f}(\omega)&=&\displaystyle\int_{-\infty}^{\infty}f(t)e^{-i\omega t}\,dt\quad &\hat{f}(\omega)&=&\displaystyle\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{i\omega t}\,dt\\[1cm]
\hat{f}(\omega)&=&\displaystyle\frac{1}{2\pi}\int_{-\infty}^{\infty}f(t)e^{i\omega t}\,dt\quad &\hat{f}(\omega)&=&\displaystyle\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-2\pi i\omega t}\,dt\end{array}.
$$

If one of these alternative definitions is used, the inverse Fourier transform in {prf:ref}`Thm:Fouriertr:InvFouriertr` also changes. In fact, for each of these choices some of the computation rules become more pretty (but others become less pretty). In general however, these choices are not really relevant, except to be able to precisely check the calculations. Always check which definition of the Fourier transform is used.

:::

:::{note}
For some functions, there is a direct connection between their Fourier and Laplace transforms. Suppose that $f$ is a function with $f(t)=0$ for $t<0$. Then for any $s>0$ we can evaluate

$$
 \mathcal{F}(f)(-is)=\int_{-\infty}^\infty f(t)e^{-i(-is)t}\,dt=\int_0^\infty f(t)e^{-st}\,dt=\mathcal{L}(f)(s).
$$

So we can think of the Laplace transform as a Fourier transform with an *imaginary* input $\omega$ (we used $\omega=-is$ here). We will see that many properties of the two transformations work very similarly. The advantage of the Laplace transform is that it converges for some functions where the Fourier transform diverges. On the other hand, the inverse formula for the Laplace transform is too hard to work with, while for the Fourier transform we have an explicit expression (though that one can still be hard to work with in practice).
:::

For many functions, finding the Fourier transform analytically is impossible as the integrals involved are too hard to evaluate. Still, there are a few imporant functions of which we can evaluate the Fourier transform by hand. Since many of these examples involve step functions, it is convenient to introduce these first.

::::::{prf:definition}
:label: Def:Fouriertr:Heaviside
For any $c$ in $\mathbb{R}$, the **unit step function** or **Heaviside function** $u_c(t)$ is given by

$$
 u_c(t)=\left\{\begin{array}{ll}0&t<c,\\ 1&t\geq c.\end{array}\right.
$$

::::::

The Heaviside function is named after the British mathematician and electrical engineer [Oliver Heaviside (1850-1925)](https://en.wikipedia.org/wiki/Oliver_Heaviside).

Let us now consider a few examples of functions of which we can evaluate the Fourier transform by hand.

::::::{prf:example} Exponentially decaying function
:label: Ex:Fouriertr:Exponential
Let $a$ be a (possibly complex) number with $\mathrm{Re}(a)>0$ and consider the function 

$$
 \displaystyle f(t)=e^{-at}u_0(t)=\left\{\begin{array}{ll}0&t<0,\\ e^{-at}&t\geq 0.\end{array}\right.
$$

Here $u_0(t)$ is the Heaviside function centered around $0$, so 

$$
 u_0(t)=\left\{\begin{array}{ll}0&t<0,\\ 1&t\geq 0.\end{array}\right.
$$

:::{figure} Images/Fig-FourierTrs-Exp.png
:name: Fig:FourierTrs:Exp

The graph of the function $f$ for some real $a>0$.
:::

Since the improper integral $\displaystyle \int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt$ has two infinite limits, we should evaluate this improper integral by splitting it up. It is convenient to split it up in the part from $-\infty$ to $0$ and the part from $0$ to $\infty$, since the function $f$ behaves differently on these parts. We can evaluate the Fourier transform of $f$ directly from the definition and we obtain

$$
 \begin{align*}\hat{f}(\omega)=&\int_{-\infty}^\infty e^{-at}u_0(t)e^{-i\omega t}\,dt\\
 =&\int_{-\infty}^0 0\cdot e^{-i\omega t}\,dt+\int_{0}^\infty e^{-at}e^{-i\omega t}\,dt\\
 =&0+\lim_{b\rightarrow\infty}\int_{0}^b e^{-at-i\omega t}\,dt\\
 =&\lim_{b\rightarrow\infty}\left[\frac{1}{-a-i\omega}e^{-at-i\omega t}\right]_0^b\\
 =&\lim_{b\rightarrow\infty}\left[\frac{1}{-a-i\omega}e^{-\mathrm{Re}(a)t}e^{-i\mathrm{Im}(a)t-i\omega t}\right]_0^b\\
 =&\frac{1}{a+i\omega}.\end{align*}
$$

In the final step we found that $\displaystyle \lim_{b\rightarrow\infty}\left[\frac{1}{-a-i\omega}e^{-\mathrm{Re}(a)b}e^{-i\mathrm{Im}(a)b-i\omega b}\right]=0$, since $\displaystyle \lim_{b\rightarrow\infty}e^{-\mathrm{Re}(a)b}=0$ as $\mathrm{Re}(a)>0$, while we have $\left|e^{-i\mathrm{Im}(a)b-i\omega b}\right|=1$ for all $b$. 

Unfortunately, since the Fourier transform of this function is complex-valued, we cannot sketch its graph.
:::::::

::::::{prf:example} Block function
:label: Ex:Fouriertr:Block
An important building block for finding the Fourier transform of more complicated functions, is the so-called **block function** or **rectangular function** $f(t)=u_{-a}(t)-u_a(t)$, where $a>0$. The naming of this function comes from the fact that its graph looks like a block, see {numref}`Fig:FourierTrs:Block`. 

:::{figure} Images/Fig-FourierTrs-Block.png
:name: Fig:FourierTrs:Block

The graph of the function $f$ when $a=1$.
:::

In order to evaluate the Fourier transform, we note that $f(t)=0$ for $t<-a$ and $t>a$, since for $t<-a$ we have both $u_{-a}(t)=0$ and $u_a(t)=0$, while for $t>a$ we have both $u_{-a}(t)=1$ and $u_a(t)=1$, which gives $f(t)=u_{-a}(t)-u_a(t)=1-1=0$. As such, the integral from $-\infty$ to $\infty$ will be the same as the one from $-a$ to $a$. In addition, for $-a\leq t<a$ we have $u_{-a}(t)=1$ and $u_a(t)=0$, which gives $f(t)=1-0=1$. Hence, we obtain

$$
 \begin{align*}\mathcal{F}(f)(\omega)=&\int_{-\infty}^\infty \left(u_{-a}(t)-u_a(t)\right)e^{-i\omega t}\,dt\\
 =&\int_{-a}^a 1\cdot e^{-i\omega t}\,dt\\
 =&\left[\frac{1}{-i\omega}e^{-i\omega t}\right]_{-a}^a\\
 =&\frac{1}{-i\omega}e^{-i\omega a}-\frac{1}{-i\omega}e^{-i\omega(-a)}\\
 =&\frac{1}{-i\omega}\left(\cos(-\omega a)+i\sin(-\omega a)\right)-\frac{1}{-i\omega}\left(\cos(\omega a)+i\sin(\omega a)\right)\\
 =&\frac{2\sin(a\omega)}{\omega}.\end{align*}
$$

The function $\mathcal{F}(f)(\omega)=\dfrac{2\sin(a\omega)}{\omega}$ is called a **sinc function**. The main reason that the sinc function is considered to be an interesting function is the fact that it is the Fourier transform of the block function. The graph of this Fourier transform is shown in {numref}`Fig:FourierTrs:BlockFT`.

:::{figure} Images/Fig-FourierTrs-BlockFT.png
:name: Fig:FourierTrs:BlockFT

The graph of the Fourier transform of the function $f$ when $a=1$.
:::

::::::

::::::{prf:example} Triangle function
:label: Ex:Fouriertr:Triangle
Consider the function $f(t)=(1-|t|)(u_{-1}(t)-u_1(t))$. Since the graph of $f$ takes the shape of a triangle with vertices $(-1,0)$, $(0,1)$ and $(1,0)$, see {numref}`Fig:FourierTrs:triangle`, this function is function is known as the **triangle function** or **tent function** (or the **hat function** if you are feeling fancy). 

:::{figure} Images/Fig-FourierTrs-Triangle.png
:name: Fig:FourierTrs:triangle

The graph of the function $f$.
:::

Just as in {prf:ref}`Ex:Fouriertr:Block`, the function $f$ is $0$ on the intervals $(-\infty,-1)$ and $(1,\infty)$. In addition, for $-1\leq t\leq 0$ we have

$$
 f(t)=(1-|t|)(u_{-1}(t)-u_1(t))=(1-(-t))(1-0)=1+t,
$$

while for $0\leq t\leq 1$ we have

$$
 f(t)=(1-|t|)(u_{-1}(t)-u_1(t))=(1-t)(1-0)=1-t.
$$

As such, we can evaluate the Fourier transform of $f$ as follows

$$
 \begin{align*}\mathcal{F}(f)(\omega)=&\int_{-\infty}^\infty (1-|t|)(u_{-1}(t)-u_1(t))e^{-i\omega t}\,dt\\
 =&\int_{-1}^0\left(1+t\right)e^{-i\omega t}\,dt+\int_0^{1}\left(1-t\right)e^{-i\omega t}\,dt. \end{align*}
$$

For both integrals, we now use integration by parts to obtain

$$
 \begin{align*}\mathcal{F}(f)(\omega) =&\int_{-1}^0\left(1+t\right)e^{-i\omega t}\,dt+\int_0^{1}\left(1-t\right)e^{-i\omega t}\,dt\\
 &=\left[\left(1+t\right)\frac{1}{-i\omega}e^{-i\omega t}\right]_{-1}^0-\int_{-1}^01\cdot \frac{1}{-i\omega}e^{-i\omega t}\,dt+\left[\left(1-t\right)\frac{1}{-i\omega}e^{-i\omega t}\right]_{0}^1-\int_{0}^1(-1)\cdot \frac{1}{-i\omega}e^{-i\omega t}\,dt\\
 &= \frac{1}{-i\omega}-\left[\frac{1}{\left(-i\omega\right)^2}e^{-i\omega t}\right]_{-1}^0-\frac{1}{-i\omega}-\left[-\frac{1}{\left(-i\omega\right)^2}e^{-i\omega t}\right]_{0}^1\\
 &=-\frac{1}{-\omega^2}+\frac{1}{-\omega^2}e^{i\omega}+\frac{1}{-\omega^2}e^{-i\omega}-\frac{1}{-\omega^2}\\
 &=-\frac{2}{-\omega^2}+\frac{1}{-\omega^2}\left(\cos(\omega)+i\sin(\omega)+\cos(-\omega)+i\sin(-\omega)\right)\\
 &=-\frac{2}{-\omega^2}+\frac{2\cos(\omega)}{-\omega^2}\\
 &=\frac{4\sin^2\left(\frac{\omega}{2}\right)}{\omega^2}.\end{align*}
$$

In the final step we used the trigonometric identity $\sin^2(x)=\frac{1}{2}-\frac{1}{2}\cos(2x)$.

:::{figure} Images/Fig-FourierTrs-TriangleFT.png
:name: Fig:FourierTrs:triangleFT

The graph of the Fourier transform of the function $f$.
:::

::::::

## Properties of the Fourier transform

In order to construct the Fourier transforms of more complicated functions, it is essential to know some general properties of the Fourier transform. Many of these properties are similar to those of the Laplace transform. The first one is that taking the Fourier transform is a linear operation.

::::::{prf:theorem} Linearity
:label: Thm:Fouriertr:Linear
For functions $f(t)$ and $g(t)$ whose Fourier transforms exist and constants  $c_{1},\,c_{2} \in \mathbb{C}$, it holds that  

$$
 {\mathcal F}\left\{c_{1} f(t) + c_{2} g(t)\right\}(\omega)=c_{1}{\mathcal F}\left\{f(t)\right\}(\omega)
 + c_{2}{\mathcal F}\left\{g(t)\right\}(\omega).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Linear`
:class: tudproof, dropdown
Since the integral is linear (even an improper one), we find for any $\omega$ that

$$
 \mathcal{F}(c_1f+c_2g)(\omega)=\int_{-\infty}^\infty (c_1f(t)+c_2g(t))e^{-i\omega t}\,dt=c_1\int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt+c_2\int_{-\infty}^\infty g(t)\,dt=c_1\mathcal{F}(f)(\omega)+c_2\mathcal{F}(g)(\omega).
$$

This yields ${\mathcal F}\left\{c_{1} f(t) + c_{2} g(t)\right\}(\omega=c_{1}{\mathcal F}\left\{f(t)\right\}(\omega)+c_{2}{\mathcal F}\left\{g(t)\right\}(\omega)$, as desired.
:::

As a consequence of {prf:ref}`Thm:Fouriertr:Linear`, we obtain that two different continuous functions can never have the same Fourier transform.

::::::{prf:corollary} 
:label: Cor:Fouriertr:Unique
If $f$ and $g$ are continuous, and $\mathcal{F}(f)=\mathcal{F}(g)$, then we have $f=g$.

::::::

:::{admonition} Proof of {prf:ref}`Cor:Fouriertr:Unique`
:class: tudproof, dropdown
From the linearity of the Fourier transform, we have have

$$
 \mathcal{F}(f-g)=\mathcal{F}(f)-\mathcal{F}(g)=0.
$$

Then since $f$ and $g$ are continuous, we obtain from {prf:ref}`Thm:Fouriertr:InvFouriertr` that

$$
 f(t)-g(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}\mathcal{F}(f-g)(\omega)e^{it\omega}\,d\omega=\frac{1}{2\pi}\int_{-\infty}^{\infty}0\cdot e^{it\omega}\,d\omega=0.
$$

Hence, we must have $f=g$, as desired.
:::

In {prf:ref}`Thm:Fouriertr:InvFouriertr` we saw that the inverse Fourier transform is very similar to the Fourier transform itself. So what happens if we apply the Fourier transform twice in a row? Then we expect to obtain something that is similar, but probably not quite the same, as the original function. Indeed, we have the following result.

::::::{prf:theorem} Duality
:label: Thm:Fouriertr:Duality
For a function $f(t)$ of which the Fourier transform and the Fourier transform of the Fourier transform exist, it holds that 

$$
 {\mathcal F}\left\{\mathcal{F}\{f\}(\omega)\right\}(t)={\mathcal F}\left\{\hat{f}(\omega)\right\}(t) =  2\pi f(-t).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Duality`
:class: tudproof, dropdown
Using {prf:ref}`Thm:Fouriertr:InvFouriertr`, we have

$$
 f(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}\hat{f}(\omega)e^{it\omega}\,d\omega
$$

for any $t$. By substituting $-t$ instead of $t$ and by multiplying the equation by $2\pi$, we obtain

$$
 2\pi f(-t)=\int_{-\infty}^{\infty}\hat{f}(\omega)e^{i(-t)\omega}\,d\omega=\int_{-\infty}^{\infty}\hat{f}(t)e^{-i\omega t}\,d\omega.
$$

The latter expression is, by definition, equal to $\mathcal{F}(\hat{f})(\omega)$. Hence, we obtain

$$
 2\pi f(-t)=\mathcal{F}(\hat{f})(\omega),
$$

as desired.
:::

[^Footnotedoppler]: This result is also related to the famous Doppler effect. For instance, when a vehicle approaches an observer the time axis is compressed, which, rougly speaking, means that we consider $f(at)$ for some $0<a<1$. If the Fourier transform of the original signal has a peak at $\omega_0$, {prf:ref}`Thm:Fouriertr:Scaling` tells us that the Fourier tranform of the moving signal has a peak at $\dfrac{\omega_0}{a}$, which is a higher number than $\omega_0$ since $0<a<1$. This means that the observer hears a higher pitch. Reversely, when the vehicle moves away, we consider $f(bt)$ for some $b>1$. In that case, the Fourier transform will have a peak at $\dfrac{\omega_0}{b}$, which gives a lower pitch than the original signal.

Recall that the Fourier transform $\mathcal{F}(f)(\omega)$ is a measure of how much of a wave with angular frequency $\omega$ is contained in the signal $f$. Now if we consider the function $g(t)=f(2t)$, then the signal goes twice as fast. If we compare the graphs of $f$ and $g$, then we obtain the graph of $g$ by compressing the one of $f$ in the $t$-direction by a factor $2$. If the Fourier transform of $f$ has a peak at a certain value $\omega_0$, then the Fourier transform of $g$ will have a peak at $2\omega_0$. This suggests that the graph of the Fourier transform of $g$ will be obtained from the one of the Fourier transform of $f$ by *stretching* it by a factor $2$ in the $\omega$-direction. However, this not is the entire story, since the amplitude of the Fourier transform also changes. In fact, we obtain the following result[^Footnotedoppler].

::::::{prf:theorem} Scaling
:label: Thm:Fouriertr:Scaling
For a function $f(t)$ whose Fourier transform exists and $a\in\mathbb{R}$ with $a\neq 0$, it holds that

$$
 {\mathcal F}\left\{f(at)\right\}(\omega)=\frac{1}{|a|}\hat{f}\left(\frac{\omega}{a}\right).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Scaling`
:class: tudproof, dropdown
The Fourier transform ${\mathcal F}\left\{f(at)\right\}(\omega)$ of the scaled function is given by

$$
 {\mathcal F}\left\{f(at)\right\}(\omega)=\int_{-\infty}^\infty f(at)e^{-i\omega t}\,dt.
$$

We first suppose that $a>0$. Then we substitute $u=at$, with $du=a\,dt$. Since $u\rightarrow\infty$ whenever $t\rightarrow\infty$ and $u\rightarrow-\infty$ whenever $t\rightarrow-\infty$, we obtain

$$
 \int_{-\infty}^\infty f(at)e^{-i\omega t}\,dt=\int_{-\infty}^\infty f(u)e^{-i\omega \frac{u}{a}}\frac{1}{a}\,du=\frac{1}{a}\int_{-\infty}^\infty f(u)e^{-i\omega \frac{u}{a}}\,du=\frac{1}{a}\hat{f}\left(\frac{\omega}{a}\right).
$$

Now we suppose that $a<0$. We again substitute $u=at$, but this time, we have $u\rightarrow-\infty$ whenever $t\rightarrow\infty$ and $u\rightarrow\infty$ whenever $t\rightarrow-\infty$. Hence, we obtain

$$
 \int_{-\infty}^\infty f(at)e^{-i\omega t}\,dt=\int_{\infty}^{-\infty}f(u)e^{-i\omega \frac{u}{a}}\frac{1}{a}\,du=-\frac{1}{a}\int_{-\infty}^\infty f(u)e^{-i\omega \frac{u}{a}}\,du=\frac{1}{|a|}\hat{f}\left(\frac{\omega}{a}\right).
$$

:::

With the linearity and scaling, we can (more easily) find some new Fourier transforms.

::::::{prf:example} Linearity and scaling
:label: Ex:Fouriertr:Linscale
Consider the function $g(t)=e^{-|t|}$. This function is the same as the function $f(t)=u_0(t)e^{-t}$ from {prf:ref}`Ex:Fouriertr:Exponential` (with $a=1$) for positive values of $t$. For negative values of $t$, the function $f$ is $0$, while $g(t)=g(|t|)$. We can use this to express $g(t)$ in terms of $f(t)$ and $f(-t)$. We claim that

$$
 g(t)=f(t)+f(-t).
$$

Indeed, for $t>0$ we have $f(t)=g(t)$ and $f(-t)=0$, while for $t<0$ we have $f(t)=0$ and

$$
 f(-t)=u_0(-t)e^{-(-t)}=e^t=e^{-|t|}=g(t).
$$

Using {prf:ref}`Thm:Fouriertr:Linear`, we obtain

$$
 \mathcal{F}(g(t))(\omega)=\mathcal{F}(f(t)+f(-t))(\omega)=\mathcal{F}(f(t))(\omega)+\mathcal{F}(f(-t))(\omega).
$$

For the Fourier tranform of $f(-t)$, we can use {prf:ref}`Thm:Fouriertr:Scaling` to obtain

$$
 \mathcal{F}(f(-t))(\omega)=\frac{1}{|-1|}\mathcal{F}(f(t))\left(\frac{\omega}{-1}\right)=\mathcal{F}(f(t))(-\omega).
$$ 

Since we have found that $\mathcal{F}(f(t))(\omega)=\dfrac{1}{1+i\omega}$ in {prf:ref}`Ex:Fouriertr:Exponential`, we obtain

$$
 \mathcal{F}(g(t))(\omega)=\mathcal{F}(f(t))(\omega)+\mathcal{F}(f(t))(-\omega)=\frac{1}{1+i\omega}+\frac{1}{1+i(-\omega)}=\frac{(1-i\omega)+(1+i\omega)}{(1+i\omega)(1-i\omega)}=\frac{2}{1+\omega^2}.
$$

::::::

We can now use the duality to find yet another Fourier transform.

::::::{prf:example} Duality
:label: Ex:Fouriertr:Duality
Consider the function $h(t)=\dfrac{1}{1+t^2}$. Note that this function is related to the function $\mathcal{F}\left(e^{-|t|}\right)(\omega)=\frac{2}{1+\omega^2}$ that we obtained in {prf:ref}`Ex:Fouriertr:Linscale`. We can now use {prf:ref}`Thm:Fouriertr:Duality` to write

$$
 2\pi e^{-|-t|}=\int_{-\infty}^\infty \frac{2}{1+\omega^2}e^{-it\omega}\,d\omega,
$$

which can be rewritten and simplified as

$$
 \pi e^{-|t|}=\int_{-\infty}^\infty \frac{1}{1+\omega^2}e^{-it\omega}\,d\omega.
$$

We now interchange the two symbols $t$ and $\omega$ to obtain

$$
 \pi e^{-|\omega|}=\int_{-\infty}^\infty \frac{1}{1+t^2}e^{-i\omega t}\,dt.
$$

The integral on the right is the Fourier transform of $h(t)=\dfrac{1}{1+t^2}$, so we obtain

$$
 \mathcal{F}\left(\frac{1}{1+t^2}\right)(\omega)=\pi e^{-|\omega|}.
$$

:::{figure} Images/Fig-FourierTrs-Exp1overtsq.png
:name: Fig:FourierTrs:Exp1overtsq

The graphs of the function $\pi e^{-|t|}$ and its Fourier transform.
::::::

Suppose a function $f$ describes an incoming light signal. Shifting the argument (so considering a function of the form $g(t)=f(t-a)$) delays the time the light reaches you, but it should not change the amount of green or blue light you see (that it, it should not change the size of the Fourier transform). It can, however, change the phase of the light. To be precise, we obtain the following result.

::::::{prf:theorem} Shift in time domain
:label: Thm:Fouriertr:Shift
For a function $f(t)$ whose Fourier transform exists and $a\in\mathbb{R}$, it holds that

$$
 {\mathcal F}\left\{f(t-a)\right\}(\omega)=e^{-ia\omega}\hat{f}(\omega).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Shift`
:class: tudproof, dropdown
Using the definition of the Fourier transform, we have

$$
 {\mathcal F}\left\{f(t-a)\right\}(\omega)=\int_{-\infty}^\infty f(t-a)e^{-i\omega t}\,dt.
$$

We use the substitution $u=t-a$. Since $u\rightarrow\infty$ whenever $t\rightarrow\infty$ and $u\rightarrow-\infty$ whenever $t\rightarrow-\infty$, we obtain

$$
 \int_{-\infty}^\infty f(t-a)e^{-i\omega t}\,dt=\int_{-\infty}^\infty f(u)e^{-\omega (u+a)}\,du=e^{-i\omega a}\int_{-\infty}^\infty f(u)e^{-i\omega u}\,du.
$$

The final integral is simply the Fourier transform of $f$, so we obtain

$$
 {\mathcal F}\left\{f(t-a)\right\}(\omega)=e^{-ia\omega}\hat{f}(\omega),
$$

as desired.


:::
:::

Since shifting $t$ amounts to multiplying the Fourier transform by a complex exponential, it makes sense that shifting $\omega$ should amount to multiplying the original function by a complex exponential as well. Indeed, we obtain the following result.

::::::{prf:theorem} Shift in frequency domain
:label: Thm:Fouriertr:Shiftfreq
For a function $f(t)$ whose Fourier transform exists and $a\in\mathbb{R}$, it holds that

$$
 {\mathcal F}\left\{e^{iat}f(t)\right\}(\omega)=\hat{f}(\omega-a).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Shift`
:class: tudproof, dropdown
Using the definition of the Fourier transform, we directly obtain

$$
 {\mathcal F}\left\{e^{iat}f(t)\right\}(\omega)=\int_{-\infty}^\infty e^{iat}f(t)e^{-i\omega t}\,dt=\int_{-\infty}^\infty f(t)e^{-i(\omega-a) t}\,dt=\mathcal{F}(f(t))(\omega-a).
$$

:::

::::::{prf:example} Shift in time domain
:label: Ex:Fouriertr:Shift
In {prf:ref}`Ex:Fouriertr:Block` we have seen that for the function $f(t)=u_{-1}(t)-u_1(t)$ we have

$$
 \hat{f}(\omega)=\frac{2\sin(\omega)}{\omega}.
$$

Now we, instead, take $g(t)=u_1(t)-u_3(t)$. This is a shifted version of $f$, since we have $g(t)=f(t-2)$. According to {prf:ref}`Thm:Fouriertr:Shift`, we must have

$$
 \hat{g}(\omega)=e^{-2i\omega}\hat{f}(\omega)=e^{-2i\omega}\frac{2\sin(\omega)}{\omega}.
$$

We could also have found this Fourier transform directly by evaluating

$$
 \begin{align*}\hat{g}(\omega)=&\int_{-\infty}^\infty \left(u_{1}(t)-u_3(t)\right)e^{-i\omega t}\,dt\\
 =&\int_{1}^3 1\cdot e^{-i\omega t}\,dt\\
 =&\left[\frac{1}{-i\omega}e^{-i\omega t}\right]_{1}^3\\
 =&\frac{1}{-i\omega}e^{-i\omega 3}-\frac{1}{-i\omega}e^{-i\omega\cdot 1}\\
 =&\frac{1}{-i\omega}e^{-2i\omega}\left(e^{-i\omega}-e^{i\omega}\right)\\
 =&\frac{1}{-i\omega}e^{-2i\omega}\left(\cos(-\omega )+i\sin(-\omega )-\cos(\omega )-i\sin(\omega )\right)\\
 =&e^{-2i\omega}\frac{2\sin(\omega)}{\omega}.\end{align*}
$$

::::::

::::::{prf:example} Shift in frequency domain
:label: Ex:Fouriertr:Shiftfreq
In {prf:ref}`Ex:Fouriertr:Exponential` we have seen that for the function $f(t)=u_0(t)e^{-t}$ we have

$$
 \hat{f}(\omega)=\frac{1}{1+i\omega}.
$$

Now we, instead, consider the function $g(t)=\sin(2t)e^{-t}u_0(t)$. Now since 

$$
 \sin(2t)=\frac{1}{2i}\left(e^{2it}-e^{-2it}\right)
$$

we have

$$
 g(t)=\frac{1}{2i}\left(e^{2it}-e^{-2it}\right)f(t).
$$

According to {prf:ref}`Thm:Fouriertr:Linear` and {prf:ref}`Thm:Fouriertr:Shift`, we must have

$$
 \hat{g}(\omega)=\frac{1}{2i}\left(\hat{f}(\omega-2)-\hat{f}(\omega+2)\right)=\frac{1}{2i}\left(\frac{1}{1+i(\omega-2)}-\frac{1}{1+i(\omega+2)}\right)=\frac{2}{-\omega^2+2i\omega+5}.
$$



::::::

An important property of the Fourier transform, is that we can relate the Fourier transforms of a function and of its derivative.


::::::{prf:theorem} Differentiation
:label: Thm:Fouriertr:Diff
For a function $f(t)$ whose Fourier transform exists and which has $\lim\limits_{t\rightarrow\pm\infty}f(t)=0$, the Fourier transform of $f'$ also exists and we have

$$
 {\mathcal F}\left\{f'(t)\right\}(\omega)=i\omega \hat{f}(\omega).
$$

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Diff`
:class: tudproof, dropdown
Using integration by parts, we find

$$
 {\mathcal F}\left\{f'(t)\right\}(\omega)=\int_{-\infty}^\infty f'(t)e^{-it\omega}\,dt=\left[f(t)e^{-it\omega}\right]_{t=-\infty}^\infty-\int_{-\infty}^\infty (-i\omega)f(t)e^{-it\omega}\,dt.
$$

We observe that $\displaystyle \lim_{t\rightarrow\pm\infty}f(t)e^{it\omega}=0$, since $\displaystyle \lim_{t\rightarrow\pm\infty}f(t)=0$ and $\left|e^{it\omega}\right|=1$. Hence, we obtain


$$
 {\mathcal F}\left\{f'(t)\right\}(\omega)=\left[f(t)e^{-it\omega}\right]_{t=-\infty}^\infty-\int_{-\infty}^\infty (-i\omega)f(t)e^{-it\omega}\,dt=0+i\omega \int_{-\infty}^\infty f(t)e^{-it\omega}\,dt=i\omega \hat{f}(\omega).
$$
:::

This means that the sometimes rather complicated operation of differentiation is nothing more than a mere multiplication on the Fourier side. Reversely, differentiation on the Fourier side of things should also give a multiplication in the time domain on account of duality. Indeed, we obtain the followin result.

::::::{prf:theorem} Multiplication by $t$
:label: Thm:Fouriertr:Multt
For a function $f(t)$ for which the Fourier transform of $tf(t)$ exists, the Fourier transform $\hat{f}(\omega)$ is differentiable and we have

$$
 \mathcal{F}\left\{tf(t)\right\}(\omega)=i\dfrac{d}{d\omega}\hat{f}(\omega).
$$
::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Multt`
:class: tudproof, dropdown
For any $\omega$, we have

$$
 \hat{f}(\omega)=\int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt.
$$

Then we differentiate both sides of the equation with respect to $\omega$ to obtain

$$
 \frac{d}{d\omega}\hat{f}(\omega)=\frac{d}{d\omega}\left[\int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt\right].
$$

Using the [Leibniz integral rule](https://en.wikipedia.org/wiki/Leibniz_integral_rule), we can take the derivative inside the integral to obtain

$$
 \frac{d}{d\omega}\hat{f}(\omega)=\int_{-\infty}^\infty \frac{d}{d\omega}\left[f(t)e^{-i\omega t}\right]\,dt=\int_{-\infty}^\infty (-it)f(t)e^{-i\omega t}\,dt.
$$

Upon taking the $-i$ to the other side of the equation and using that $\dfrac{1}{-i}=i$, we obtain

$$
 i\frac{d}{d\omega}\hat{f}(\omega)=\int_{-\infty}^\infty tf(t)e^{-i\omega t}\,dt=\mathcal{F}\left\{tf(t)\right\}(\omega),
$$

as desired.
:::

::::::{prf:example} Differentiation
:label: Ex:Fouriertr:Differentiation
Consider the function 

$$
 f(t)=\frac{t}{(1+t^2)^2}.
$$

This function is related to the function $h$ from {prf:ref}`Ex:Fouriertr:Duality`, since we have

$$
 h'(t)=-\frac{2t}{(1+t^2)^2}=-2f(t).
$$

So on account of {prf:ref}`Thm:Fouriertr:Diff`, we obtain

$$
 \hat{f}(\omega)=-\frac{1}{2}i\omega\hat{h}(\omega)=-\frac{1}{2}i\omega\pi e^{-|\omega|}.
$$ 
::::::

{prf:ref}`Thm:Fouriertr:Multt` can be used to find one of the most important Fourier transforms, namely the one of Gaussian functions. 

::::::{prf:example} Gaussian
:label: Ex:Fouriertr:Gaussian
A **Gaussian function** is a function of the form 

$$
 f(x)=a\exp\left(-\frac{(x-b)^2}{2c^2}\right).
$$

It is named after the German mathematician [Carl Friedrich Gauss (1777-1855)](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss). Its graph has a characteristic shape, called the "bell curve". These functions play a very important role in probability and statistics, as they can be used to describe random variables with a normal distribution.

For simplicity, we here consider the Gaussian

$$
 f(t)=e^{-at^2}
$$

for some constant $a>0$. According to {prf:ref}`Thm:Fouriertr:Multt`, we have

$$
 \frac{d}{d\omega}\hat{f}(\omega)=\frac{1}{i}\mathcal{F}\left\{te^{-at^2}\right\}(\omega)=\frac{1}{i}\mathcal{F}\left\{-\frac{1}{2a}\frac{d}{dt}e^{-at^2}\right\}(\omega).
$$

Using {prf:ref}`Thm:Fouriertr:Linear` and {prf:ref}`Thm:Fouriertr:Diff`, we find

$$
 \frac{d}{d\omega}\hat{f}(\omega)=-\frac{1}{i}\frac{1}{2a}i\omega\mathcal{F}\left\{e^{-at^2}\right\}=-\frac{\omega}{2a}\hat{f}(\omega).
$$

As such, the function $\hat{f}$ is a solution to the differential equation

$$
 y'(\omega)=-\frac{\omega}{2a}y(\omega).
$$

This is a linear, first order differential equation and (using an integrating factor), we obtain the solution

$$
 \hat{f}(\omega)=Ce^{-\frac{\omega^2}{4a}}
$$

for some (as of yet) unknown constant $C$. In order to find this $C$, we note that

$$
 C=\hat{f}(0)=\int_{-\infty}^\infty e^{-at^2}\,dt.
$$

This remaining intgral is a standard integral and we find that

$$
 C=\int_{-\infty}^\infty e^{-at^2}\,dt=\sqrt{\frac{\pi}{a}}.
$$

As such, we find that

$$
 \hat{f}(\omega)=\sqrt{\frac{\pi}{a}}e^{-\frac{\omega^2}{4a}}.
$$

This means that the Fourier transform of a Gaussian is again a Gaussian. 

[^FootnoteUncertainty]: Heisenberg’s uncertainty principle, stating that you cannot know the location and speed of a particle at once, is related to this fact. If we are way too unspecific: In quantum mechanics there is a function $\psi$, called the wave function, indication the location of a particle, while the Fourier transform of $\psi$ gives its speed. The more concentrated this function in one peak the better you know its location, and similarly for $\mathcal{F}(\psi)$ and the speed. But the more spiked you make $\psi$ the more spread $\mathcal{F}(\psi)$ has to be and vice versa. So you can never be certain about both location and speed at the same time.


Note that the graph of $f(t)=e^{-at^2}$ is very narrow/spiked when $a$ is very large, while it is rather flat if $a$ is rather flat. As we would expect from {prf:ref}`Thm:Fouriertr:Scaling`, this relation is inverted for the Fourier transform.[^FootnoteUncertainty]

:::{figure} Images/Fig-FourierTrs-Gaussian.png
:name: Fig:FourierTrs:Exp

The graph of two Gaussians and their Fourier transforms. The graph of the red function is more spread in the time domain, while it is narrower in the Fourier domain.
:::

::::::

So far, we have computed a lot of Fourier transforms, but not a lot of inverse Fourier transforms. So as our final example of this subsection, we will evaluate an inverse Fourier transform.

::::::{prf:example} Inverse Fourier transform
:label: Ex:Fouriertr:PFD
Suppose we want to try to find the inverse Fourier transform of 

$$
 \hat{g}(\omega)=\frac{1}{3+2i\omega+\omega^2}.
$$

The Fourier transform that most resembles this one is the one of the function $f(t)=e^{-t}u_0(t)$ from {prf:ref}`Ex:Fouriertr:Linscale`, which is given by

$$
 \mathcal{F}\left\{e^{-t}u_0(t)\right\}(\omega)=\dfrac{1}{1+i\omega}.
$$

In order to make connect the function $g$ to this known Fourier transform, we perform a partial fraction decomposition. For this we note that 

$$
 3+2i\omega+\omega^2=3+2i\omega-(i\omega)^2=-(i\omega+1)(i\omega-3)
$$

so we write

$$
 \hat{g}(\omega)=\frac{1}{3+2i\omega+\omega^2}=\frac{A}{i\omega+1}+\frac{B}{-\omega-3}.
$$

Solving for $A$ and $B$, we find $A=\dfrac{1}{4}$ and $B=-\dfrac{1}{4}$, so we have

$$
 \hat{g}(\omega)=\dfrac{1}{4}\frac{1}{i\omega +1}-\dfrac{1}{4}\frac{1}{i\omega-3}.
$$

To let it more closely resemble $\dfrac{1}{i\omega+1}$, we write

$$
 \hat{g}(\omega)=\dfrac{1}{4}\frac{1}{i\omega +1}-\dfrac{1}{4}\frac{\frac{1}{-3}}{\frac{i\omega}{-3}+1}=\dfrac{1}{4}\frac{1}{i\omega +1}+\dfrac{1}{12}\frac{1}{\frac{i\omega}{-3}+1}.
$$

Now we note that

$$
 \frac{1}{12}\frac{1}{\frac{i\omega}{-3}+1}=\frac{1}{4}\frac{1}{|-3|}\hat{f}\left(\frac{\omega}{-3}\right).
$$

As such, we have

$$
 g(\omega)=\frac{1}{4}\hat{f}\left(\omega\right)+\frac{1}{4}\frac{1}{|-3|}\hat{f}\left(\frac{\omega}{-3}\right).
$$

Hence, with use {prf:ref}`Thm:Fouriertr:Scaling` we obtain that the inverse Fourier transform $g$ of $\hat{g}$ is given by

$$
 g(t)=\frac{1}{4} f(t)+\frac{1}{4}f(-3t)=\frac{1}{4}e^{-t}u_0(t)+\frac{1}{4}e^{3t}u_0(-3t)=\left\{\begin{array}{ll}\frac{1}{4}e^{3t},\quad &t<0;\\[0.4cm] \frac{1}{4}e^{-t},\quad&t\geq 0.\end{array}\right.
$$

::::::

As a final imporant property of the Fourier transform is that it conserves energy. This result is known as the **Plancherel theorem**, or sometimes as the **Parseval-Plancherel identity** or **Parseval's theorem** (though that one usually refers to a version of this result for *Fourier series*).  It is named after the Swiss mathematician [Michel Plancherel (1885-1967)](https://en.wikipedia.org/wiki/Michel_Plancherel), with the alternative names coming from the French mathematician [Marc-Antoine Parseval (1755-1836)](https://en.wikipedia.org/wiki/Marc-Antoine_Parseval).

::::::{prf:theorem} Plancherel
:label: Thm:Fouriertr:Plancherel
Suppose $f:\mathbb{R}\rightarrow\mathbb{C}$ is a function of which the Fourier transform exists. Then we have

$$
 \int_{-\infty}^\infty |f(t)|^2\,dt=\frac{1}{2\pi}\int_{-\infty}^\infty |\hat{f}(\omega)|^2\,d\omega.
$$

whenever the integral on the left-hand side of this equation converges.

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Plancherel`
:class: tudproof, dropdown
For any complex number $z$, we have $|z|^2=z\overline{z}$, where $\overline{z}$ is the complex conjugate of $z$. Using the definition of the Fourier transform and {prf:ref}`Thm:Fouriertr:InvFouriertr`, we then obtain

\begin{align*}
 \int_{-\infty}^\infty |f(t)|^2\,dt=&\int_{-\infty}^\infty f(t)\overline{f(t)}\,dt\\
 =&\int_{-\infty}^\infty f(t)\frac{1}{2\pi}\int_{-\infty}^\infty\overline{\hat{f}(\omega)e^{it\omega}}\,d\omega\,dt\\
 =&\frac{1}{2\pi}\int_{-\infty}^\infty \int_{-\infty}^\infty f(t)\overline{\hat{f}(\omega)}e^{-it\omega}\,d\omega\,dt\\
 =&\frac{1}{2\pi}\int_{-\infty}^\infty \int_{-\infty}^\infty f(t)\overline{\hat{f}(\omega)}e^{-it\omega}\,dt\,d\omega\\
 =&\frac{1}{2\pi}\int_{-\infty}^\infty \int_{-\infty}^\infty f(t)e^{-it\omega}\,dt \overline{\hat{f}(\omega)}\,d\omega\\
 =&\frac{1}{2\pi}\int_{-\infty}^\infty \hat{f}(\omega) \overline{\hat{f}(\omega)}\,d\omega\\
 =&\frac{1}{2\pi}\int_{-\infty}^\infty |\hat{f}(\omega)|^2\,d\omega.
\end{align*}

:::

The interpretation of {prf:ref}`Thm:Fouriertr:Plancherel` is as follows. If the function $f$ represents a wave, then the integral $\displaystyle \int_{-\infty}^\infty |f(t)|^2\,dt$ represents the total energy contained in the wave. The theorem then states that we can obtain this energy by adding up the energies of the waves of differing frequencies, which is represented by $\displaystyle \int_{-\infty}^\infty |\hat{f}(\omega)|^2\,d\omega$.

Perhaps suprisingly, we can use this result to evaluate complicated improper integrals.

::::::{prf:example} 
:label: Ex:Fouriertr:Plancherel
Suppose we want to evaluate the improper integral

$$
 \int_{-\infty}^\infty \frac{\sin(x)^2}{x^2}\,dx.
$$

Without using the Fourier transform, this integral is very hard to evaluate, since it has two infinite limits and, more importantly, there is no way to express the antiderivative of $\dfrac{\sin(x)^2}{x^2}$ in terms of elementary functions. Fortunately, we know from {prf:ref}`Ex:Fouriertr:Block` that the function $\hat{f}(\omega)=\dfrac{2\sin(\omega)}{\omega}$ is the Fourier transform of the block function $f(t)=u_{-1}(t)-u_1(t)$. Then we see that

$$
 \int_{-\infty}^\infty \frac{\sin(x)^2}{x^2}\,dx=\frac{1}{4}\int_{-\infty}^\infty \left(\frac{2\sin(x)}{x}\right)^2\,dx=\frac{1}{4}\int_{-\infty}^\infty \left|\hat{f}(x)\right|^2\,dx.
$$

On account of {prf:ref}`Thm:Fouriertr:Plancherel`, we can now, instead, evaluate the much easier integral

\begin{align*}
 \int_{-\infty}^\infty \frac{\sin(x)^2}{x^2}\,dx=&\frac{1}{4}\int_{-\infty}^\infty \left|\hat{f}(x)\right|^2\,dx\\
 =&2\pi\frac{1}{4}\int_{-\infty}^\infty \left|f(t)\right|^2\,dt\\
 =&\frac{\pi}{2}\int_{-\infty}^\infty\left(u_{-1}(t)-u_1(t)\right)^2\,dt\\
 =&\frac{\pi}{2}\int_{-1}^1\left(1\right)^2\,dt\\
 =&\frac{\pi}{2}\cdot 2\\
 =&\pi.
\end{align*}

::::::



## Convolution and the Dirac delta

Sometimes it is possible to write the Fourier transform of an unknown function as the product of the Fourier transforms of two known functions, i.e. we know that $\hat{f}=\hat{g}\hat{h}$ for some known functions $g$ and $h$, while $f$ is unknown. How can we take the inverse Fourier transform in such a setting? What does the unknown function $f$ have to do with the known functions $g$ and $h$? It turns out that $f$ is the so-called **convolution product** of $g$ and $h$, so let us define what we mean by that.

::::::{prf:definition} 
:label: Def:Fouriertr:Conv
Given two functions $f:\mathbb{R}\rightarrow\mathbb{R}$ and $g:\mathbb{R}\rightarrow\mathbb{R}$, their **convolution product** $f\ast g$ is given by

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau.
$$

This convolution product is defined whenever the integral converges for all values of $t$.

::::::

As promised, the Fourier transform of the convolution product equals the product of the Fourier transforms, as the following theorem shows.

::::::{prf:theorem} 
:label: Thm:Fouriertr:Conv
For functions $f(t)$ and $g(t)$ whose Fourier transform exist, we have that 

$$
 {\mathcal F}\left\{f\ast g\right\}(\omega)=\hat{f}(\omega)\hat{g}(\omega)
$$

and

$$
 2\pi{\mathcal F}\left\{f(t)g(t)\right\}(\omega)=(\hat{f}\ast\hat{g})(\omega).
$$

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Conv`
:class: tudproof, dropdown
From the definition we obtain

$$
 \hat{f}(\omega)\hat{g}(\omega)=\int_{-\infty}^\infty f(\tau)e^{-i\tau\omega}\,d\tau\int_{-\infty}^\infty g(\sigma)e^{-i\sigma\omega}\,d\sigma.
$$

Here we used $\tau$ and $\sigma$ instead of the usual $t$ as variables in the integrals to distinguish them from each other. Then we can rewrite this product of two integrals as an iterated integral by writing

$$
 \hat{f}(\omega)\hat{g}(\omega)=\int_{-\infty}^\infty \int_{-\infty}^\infty f(\tau)g(\sigma)e^{-i\sigma\omega-i\tau\omega}\,d\tau\,d\sigma .
$$

Now we use the substitution $\sigma=t-\tau$ (to be clear, we replace $\sigma$ by $t-\tau$ and integrate over $t$ instead of over $\sigma$). Then we see that $t\rightarrow\pm\infty$ precisely when $\sigma\rightarrow\pm\infty$. In addition, we note that

$$
 e^{-i\sigma\omega-i\tau\omega}=e^{-i(t-\tau)\omega-i\tau\omega}=e^{-it\omega}.
$$

Hence, we obtain

$$
 \hat{f}(\omega)\hat{g}(\omega)=\int_{-\infty}^\infty \int_{-\infty}^\infty f(\tau)g(t-\tau)e^{-it\omega}\,d\tau\,dt=\int_{-\infty}^\infty (f\ast g)(t)e^{-it\omega}\,dt={\mathcal F}\left\{f\ast g\right\}(\omega).
$$

The other identity follows by combining the first one with {prf:ref}`Thm:Fouriertr:Duality`.
:::

:::{note}
In the context of Laplace transforms, one usually considers the product of two functions $f:[0,\infty)\rightarrow\mathbb{R}$ and $g:[0,\infty)\rightarrow\mathbb{R}$ to be given by

$$
 (f\ast g)_{\mathrm{half}}(t)=\int_0^t f(t-\tau)g(\tau)\,d\tau=\int_0^t f(\tau)g(t-\tau)\,d\tau.
$$

We use the subscript $\mathrm{half}$ to distinguish between the two definitions of the convolution. While these definitions look different, they actually work very similar. Indeed, if we extend the functions $f$ and $g$ that are only defined on the halfline $[0,\infty)$ to the full real line by setting

$$
 f(t)=g(t)=0
$$

for $t<0$, then the convolution integral from {prf:ref}`Def:Fouriertr:Conv` becomes

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau=\int_0^t f(\tau)g(t-\tau)\,d\tau=(f\ast g)_{\mathrm{half}}(t),
$$

since $f(\tau)=0$ for $\tau\leq 0$ and $g(t-\tau)=0$ for $\tau\geq t$. 

:::

::::::{prf:example} 
:label: Ex:Fouriertr:Conv
Consider the functions

$$
 f(t)=u_{-1}(t)-u_1(t)
$$

and

$$
 g(t)=u_{-3}(t)-u_2(t).
$$

Our goal is to find the convolution product $f\ast g$. By definition, this is given by the integral

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau.
$$

The integrand of this integral (the function we are integrating) is either $1$, when both $f(\tau)=g(t-\tau)=1$, or $0$, if either $f(\tau)=0$ or $g(t-\tau)=0$. On which intervals the integrand is $0$ depends on the value of $t$. To establish where this is the case, it is useful to sketch $f(\tau)$, $g(t-\tau)$ and $f(\tau)g(t-\tau)$. The area below the latter graph is the desired convolution product. We start with the sketches when $t=0$, see {numref}`Fig:FourierTrs:Convt0`.

:::{figure} Images/Fig-FourierTrs-Convt0.png
:name: Fig:FourierTrs:Convt0

The graph of the functions $f(\tau)$, $g(t-\tau)$ and $f(\tau)g(t-\tau)$ for $t=0$.
:::

If $t$ increases, the graph of $g(t-\tau)$ moves to the right, while if $t$ decreases it moves to the left. For very negative values of $t$, we have $t+3<-1$, so the regions where the graphs of $f(\tau)$ and $g(t-\tau)$ are nonzero do not overlap. As such, the convolution product equals $0$ for these values of $t$. To be precise, this is the case when $t<-4$.

Now if we start at $t=-4$ and increase $t$, the two regions where the graphs of $f(\tau)$ and $g(t-\tau)$ are nonzero start to overlap. We then obtain the situation on the left half of {numref}`Fig:FourierTrs:Convothert`. In particular, we have that both $f(\tau)$ and $g(t-\tau)$ are nonzero whenever $-1\leq \tau\leq t+3$. In that case, we obtain the convolution product

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau=\int_{-1}^{t+3}1\,d\tau=t+4.
$$

As we increase $t$, the situation changes when $t+3$ passes $1$, i.e. at $t=-2$. In that case, we obtain the situation from {numref}`Fig:FourierTrs:Convt0`. Then the convolution product becomes

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau=\int_{-1}^{1}1\,d\tau=2.
$$

Then, if we increase $t$ even further, the situation will change again when $t-2$ becomes $-1$, i.e at $t=1$. In that case, we obtain the situation on the right half of {numref}`Fig:FourierTrs:Convothert` and we evaluate

$$
 (f\ast g)(t)=\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau=\int_{t-2}^{1}1\,d\tau=3-t.
$$

The final change is when $t-2$ becomes $1$, i.e. at $t=3$. In that case, the regions where the graphs of $f(\tau)$ and $g(t-\tau)$ are nonzero do not overlap again, so the convolution product is $0$ again.

Combining all of these computations, we obtain

$$
 (f\ast g)(t)=\left\{\begin{array}{l}0,\quad&t\leq -4,\\ t+4,\quad&-4<t\leq-2\\ 2,\quad& -2<t\leq1\\ 3-t,\quad&1<t\leq 3,\\ 0,\quad& 3<t.\end{array}\right.
$$

:::{figure} Images/Fig-FourierTrs-Convothert.png
:name: Fig:FourierTrs:Convothert

The graph of the functions $f(\tau)$, $g(t-\tau)$ and $f(\tau)g(t-\tau)$ for $t=-3$ (left) and for $t=2$ (right).
:::

Finally, from {prf:ref}`Ex:Fouriertr:Block` we find that the Fourier transform of $f$ is given by

$$
 \hat{f}(\omega)=\frac{2\sin(\omega)}{\omega}.
$$

For the Fourier transform of $g$, we note that $g(t)=h\left(t+\frac{1}{2}\right)$, where

$$
 h(t)=u_{-\frac{5}{2}}(t)-u_{\frac{5}{2}}(t).
$$

As such, we obtain from {prf:ref}`Thm:Fouriertr:Shift` that

$$
 \hat{g}(\omega)=e^{-i\left(-\frac{1}{2}\right)\omega}\hat{h}(\omega)=e^{\frac{i\omega}{2}}\frac{2\sin\left(\frac{5}{2}\omega\right)}{\omega}.
$$

Combining these, we obtain from {prf:ref}`Thm:Fouriertr:Conv` that the Fourier transform of the convolution product $f\ast g$ is given by

$$
 \mathcal{F}\left(f\ast g\right)(\omega)=\hat{f}(\omega)\hat{g}(\omega)=\frac{2\sin(\omega)}{\omega}e^{\frac{i\omega}{2}}\frac{2\sin\left(\frac{5}{2}\omega\right)}{\omega}=\frac{4\sin(\omega)\sin\left(\frac{5}{2}\omega\right)e^{\frac{i\omega}{2}}}{\omega^2}.
$$


::::::

The convolution product has some useful properties.

::::::{prf:theorem} 
:label: Thm:Fouriertr:Convcomputation
Let $f$, $g$ and $h$ be functions and $a$ and $b$ be real numbers. Then we have

- $(f\ast g)\ast h=f\ast(g\ast h)$,
- $(af+bg)\ast h=a(f\ast h)+b(g\ast h)$,
- $f\ast g=g\ast f$.

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Convcomputation`
:class: tudproof, dropdown
For the first property, we have by definition

\begin{align*}
 ((f\ast g)\ast h)(t)=&\int_{-\infty}^\infty (f\ast g)(\tau)h(t-\tau)\,d\tau\\
 =&\int_{-\infty}^\infty\int_{-\infty}^\infty f(\sigma)g(\tau-\sigma)\,d\sigma h(t-\tau)\,d\tau\\
 =&\int_{-\infty}^\infty\int_{-\infty}^\infty f(\sigma)g(\tau-\sigma) h(t-\tau)\,d\sigma\,d\tau\\
 =&\int_{-\infty}^\infty\int_{-\infty}^\infty f(\sigma)g(\tau-\sigma) h(t-\tau)\,d\tau\,d\sigma\\
 =&\int_{-\infty}^\infty f(\sigma)\int_{-\infty}^\infty g(\tau-\sigma) h(t-\tau)\,d\tau\,d\sigma\\
 =&\int_{-\infty}^\infty f(\sigma)\int_{-\infty}^\infty g(\tau) h(t-\sigma-\tau)\,d\tau\,d\sigma\\
 =&\int_{-\infty}^\infty f(\sigma)(g\ast h)(t-\sigma)\,d\sigma\\
 =&(f\ast(g\ast h))(t).
\end{align*}

For the second property, we have

\begin{align*}
 ((af+bg)\ast h)(t)=&\int_{-\infty}^\infty (af+ bg)(\tau)h(t-\tau)\,d\tau\\
 =&a\int_{-\infty}^\infty  f(\tau) h(t-\tau)\,d\tau+b\int_{-\infty}^\infty g(\tau) h(t-\tau)\,d\tau\\
 =&a(f\ast h)(t)+b(g\ast h)(t).
\end{align*}

Finally, for the third property we have, using the substitution $\sigma=t-\tau$,

\begin{align*}
 (f\ast g)(t)=&\int_{-\infty}^\infty f(\tau)g(t-\tau)\,d\tau\\
 =&\int_{\infty}^{-\infty} f(t-\sigma)g(\sigma)(-1)\,d\sigma\\
 =&\int_{-\infty}^\infty g(\sigma)f(t-\sigma)\,d\sigma\\
 =&(g\ast f)(t).
\end{align*}
:::

The convolution product smoothens out functions. That is, you can typically take more derivatives of the convolution product than you can of one of the original functions. This follows from the following result.

::::::{prf:theorem} 
:label: Thm:Fouriertr:Convsmooth
If the convolution product $f\ast g$ exists and either $f$ or $g$ is differentiable, $f\ast g$ is differentiable and we have

$$
 \frac{d}{dt}\left(f\ast g\right)=\frac{df}{dt}\ast g=f\ast \frac{dg}{dt},
$$

whenever each of the derivatives $\dfrac{d}{dt}$ or $\dfrac{dg}{dt}$ exists.

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Convsmooth`
:class: tudproof, dropdown
According to {prf:ref}`Thm:Fouriertr:Conv`, the Fourier transform of $f\ast g$ is given by $\hat{f}\hat{g}$. On account of {prf:ref}`Thm:Fouriertr:Diff`, differentiation in the time domain is the same as multiplication by $i\omega$ in the frequency domain and we have

$$
 i\omega (\hat{f}\hat{g})=(i\omega \hat{f})\hat{g}=\hat{f}(i\omega \hat{g}).
$$

Taking the inverse Fourier transform gives the desired result.

:::


Recall that the **Dirac delta function** $\delta(t)$ is a "function" satisfying $\delta(t)=0$ for $t\neq 0$ and

$$
 \int_{-\infty}^\infty \delta(t)\,dt=1.
$$

The reason why we call it a "function" instead of an actual function, is that in order for the integral property to be true, $\delta(0)$ would need to be $\infty$, but no actual function has that property. Still, the delta function behaves like a function in all other respect. The usual purpose of the delta function is to model very short pulses. For any function $f$ which is continuous at a point $a$, we have the important integral property

$$
 \int_{-\infty}^\infty f(t)\delta(t-a)\,dt=f(a).
$$

Even though the delta function is not an actual function, we can still find its Fourier transform. This is not very
surprising, since finding a Fourier transform involves integrating, which is the one thing we can do with delta functions.

::::::{prf:theorem} 
:label: Thm:Fouriertr:Delta
The Fourier transform of the Dirac delta function equals the constant function $1$:

$$
 \mathcal{F}(\delta(t))(\omega)=1.
$$

Reversely, the Fourier transform of the constant function $1$ is a multiple of the Dirac delta function:

$$
 \mathcal{F}(1)(\omega)=2\pi\delta(\omega).
$$
::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Delta`
:class: tudproof, dropdown
We obtain

$$
 \mathcal{F}(\delta(t))(\omega)=\int_{-\infty}^\infty \delta(t)e^{-i\omega t}\,dt=e^{-i\omega\cdot 0}=1.
$$

The second identity follows from {prf:ref}`Thm:Fouriertr:Duality`.
:::

As a consequence, we can find the convolution of the delta function with most other functions.

::::::{prf:theorem} 
:label: Thm:Fouriertr:Deltaconv
For any continuous function $f$ we have

$$
 \delta \ast f=f.
$$

::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Delta`
:class: tudproof, dropdown
By definition, we have

$$
 (\delta \ast f)(t)=\int_{-\infty}^\infty\delta(\tau)f(t-\tau)\,d\tau=f(t-0)=f(t).
$$

The proof is even quicker if the function $f$ has a Fourier transform $\hat{f}$. In that case, we obtain from {prf:ref}`Thm:Fouriertr:Conv` and {prf:ref}`Thm:Fouriertr:Delta` that

$$
 \mathcal{F}(\delta\ast f)(\omega)=\hat{f}(\omega)\mathcal{F}(\delta)(\omega)=\hat{f}(\omega)\cdot 1=\hat{f}(\omega).
$$

Since the Fourier transform does not change, we must have $\delta\ast f=f$.
:::

Recall that the Fourier transform is used mostly for finding which frequencies are present in a signal. This means that it is very natural to consider the fourier transforms of the sine and cosine functions. Since we have not covered these yet, let us quickly do so (we will see why we postponed them below).

::::::{prf:example} Sine and cosine
:label: Thm:Fouriertr:Sincos
In order to find the Fourier transforms of the sine and cosine, we first consider the complex exponential

$$
 f(t)=e^{iat}
$$

for some $a>0$. Then we can write

$$
 f(t)=e^{iat}\cdot 1.
$$

It may seem strange to write the function like this, but it means that we can use the rules that we have established so far. Indeed, {prf:ref}`Thm:Fouriertr:Shiftfreq` tells us that the Fourier transform of $f$ is a shifted version of the one of the constant function $1$. The Fourier transform of the constant function $1$ is $2\pi\delta(\omega)$ on account of {prf:ref}`Thm:Fouriertr:Delta`. So we find that

$$
 \hat{f}(\omega)=2\pi\delta(\omega-a).
$$

We can use this to find the Fourier transforms of $g(t)=\cos(at)$ and $h(t)=\sin(at)$. For this we notice that

$$
 g(t)=\frac{f(t)+f(-t)}{2},\qquad h(t)=\frac{f(t)-f(-t)}{2i}.
$$

On account of {prf:ref}`Thm:Fouriertr:Linear` and {prf:ref}`Thm:Fouriertr:Scaling` we obtain

$$
 \hat{g}(\omega)=\pi\left(\delta(\omega-a)+\delta(\omega+a)\right)
$$

and

$$
 \hat{g}(\omega)=-i\pi\left(\delta(\omega-a)-\delta(\omega+a)\right).
$$

This means that the Fourier transforms of $g(t)=\cos(at)$ and $h(t)=\sin(at)$ both consist of a peak at $-a$ and one at $a$. This should not come as a surprise: these two functions have a single angular frequence, which is $a$, so we should those and only see those (and we always see the negative version as well). 

::::::

It is important to note that we use the full time range from $-\infty$ to $\infty$ to determine the Fourier transform. In practice however, it is impossible to measure a signal on an infinite time range. So what we usually do, is measure the signal on a finite time interval and take the Fourier transform of that piece of signal. If we measure long enough (to at least have caputered a full period of the wave), the Fourier transforms of the original signal and the measured signal will be similar, though not entirely the same.

For instance, consider the function $f(t)=\cos(t)$. According to {prf:ref}`Thm:Fouriertr:Sincos`, its Fourier transform has peaks at $\omega=-1$ and $\omega=1$, while it $0$ everywhere else. Suppose we measure this signal from $t=-10\pi$ to $t=10\pi$ (we choose a symmetric integral for convenience). This means that we are actually looking at the Fourier transform of the signal

$$
 g(t)=f(t)(u_{-10\pi}(t)-u_{10\pi}(t)).
$$

It can be shown that

$$
 \hat{g}(\omega)=\frac{2\omega\sin(10\pi \omega)}{\omega^2-1}.
$$

The graph of this Fourier transform is shown in {numref}`Fig:FourierTrs:Cutoffcos`.

:::{figure} Images/Fig-FourierTrs-Cutoffcos.png
:name: Fig:FourierTrs:Cutoffcos

The graph of the Fourier transform $\hat{g}(\omega)$.
:::

We see that we still have peaks at $\omega=-1$ and $\omega=1$, but they are no longer infinitely high. In addition, the function $\hat{g}$ is not $0$ for most other values of $\omega$. Still, the difference in amplitude between the values $\omega=-1,\omega=1$ and the other values of $\omega$ is very significant, so using a finite time interval still allows us to find the relevant frequencies in practice.

In addition, it is impossible, in practice, to measure a signal at **all** time points in a given time interval. Instead, we usually measure the signal at different timepoints in the time interval. Such a measurement is known as a **sample**. The **sampling frequency** or **sampling rate** is the frequency of these measurements. Then, the measurements are connected together by means of an interpolation procedure.

It is important to keep in mind that you need enough data points to fully capture the behaviour of the signal. If the number of samples is too low, you might encounter a phenomenon known as **aliasing**. More specifically, aliasing means that the reconstructed signal from the sample contains frequencies (i.e. peaks in the Fourier transform) that the original signal did not have. Aliasing occurs whenever there are less than two samples per period of the signal. Here, we will not delve deeper in this subject, but it is a very important concept to keep in mind when using the Fourier transform in practice.

:::{figure} Images/Gif-FourierTrs-WagonWheelEffect.gif
:name: Fig:FourierTrs:WagonWheelEffect

A well-known type of aliasing is known as the **wagon wheel effect**. In this animation, the camera, which has a constant shutter speed, moves to the right and its velocity increases by a fixed rate. This means that the objects appear to be sliding to the left. Halfway through the loop, the objects appear to suddenly shift and head to the right. This happens because the sampling rate has become too small compared to the motion of the objects, causing the positive frequency to be perceived as a negative one.

This animation originates from https://en.wikipedia.org/wiki/Aliasing.
:::

## Table of Fourier transforms

We collect some of the most important Fourier transforms we have obtained so far in the following table. Of course, there are more functions of which the Fourier transform is known analytically, so this is not an exhaustive list.

```{table} Standard Fourier transforms.
:widths: auto
:align: center
:name: Tab:Fouriertr:standard

|Function|Fourier transform|Parameter value|As seen in
|-|-|-|-|
|$e^{-at}u_0(t)$|$\dfrac{1}{a+i\omega}$|$\mathrm{Re}(a)>0$|{prf:ref}`Ex:Fouriertr:Exponential`|
|$u_{-a}(t)-u_a(t)$|$\dfrac{2\sin(a\omega)}{\omega}$|$a>0$|{prf:ref}`Ex:Fouriertr:Block`|
|$(1-\vert t\vert)(u_{-1}(t)-u_1(t))$|$\dfrac{4\sin^2\left(\frac{\omega}{2}\right)}{\omega^2}$|N.A.|{prf:ref}`Ex:Fouriertr:Triangle`|
|$e^{-\vert t\vert}$|$\dfrac{2}{1+\omega^2}$|N.A.|{prf:ref}`Ex:Fouriertr:Linscale`|
|$\dfrac{1}{1+t^2}$|$\pi e^{-\vert \omega\vert }$|N.A.|{prf:ref}`Ex:Fouriertr:Duality`|
|$e^{-at^2}$|$\sqrt{\dfrac{\pi}{a}}e^{-\frac{\omega^2}{4a}}$|$a>0$|{prf:ref}`Ex:Fouriertr:Gaussian`|
|$\delta(t)$|$1$|N.A.|{prf:ref}`Thm:Fouriertr:Delta`|
|$1$|$2\pi\delta(\omega)$|N.A.|{prf:ref}`Thm:Fouriertr:Delta`|
|$e^{iat}$|$2\pi\delta(\omega-a)$|$a>0$|{prf:ref}`Thm:Fouriertr:Sincos`|
|$\cos(at)$|$\pi\left(\delta(\omega-a)+\delta(\omega+a)\right)$|$a>0$|{prf:ref}`Thm:Fouriertr:Sincos`|
|$\sin(at)$|$-i\pi\left(\delta(\omega-a)-\delta(\omega+a)\right)$|$a>0$|{prf:ref}`Thm:Fouriertr:Sincos`|
```


## Differential equations and Fourier transforms

Just like the Laplace transform, the Fourier transform can, in principle, be used to find solutions of differential equations. However, we will see that in most cases we can only find particular solutions, while we need to use other techniques to find the general solution. Let us see how this technique works by considering an example.

::::::{prf:example} 
:label: Ex:Fouriertr:Diffhom
Consider the differential equation

$$
 y''+2y'+5y=0.
$$

Of course, we already know how to solve this equation, but let us see how we could, alternatively, use the Fourier transform to find the solution. We take the Fourier transform of both sides of the equation. By {prf:ref}`Thm:Fouriertr:Diff`, the Fourier transform of a derivative just means multiplication by $i\omega$. Hence, we obtain

$$
 (i\omega)^2+2(i\omega)\hat{y}+5\hat{y}=0.
$$

The most important observation here is that this is no longer a differnetial equation for $\hat{y}$, as there are no derivatives anymore. As such, it seems much easier to solve this equation in the Fourier domain, so let us try to do this. We first rewrite the equation to

$$
 \left(-\omega^2+2i\omega+5\right)\hat{y}=0.
$$

Since we are trying to solve for $\hat{y}$, we only obtain $\hat{y}=0$, which gives $y=0$. This function certainly is a solution of the differential equation, but it is not the only one. However, they do not seem to be present here in the Fourier domain, so how can that be? The unfortunate answer is that these other solutions do not have a convergent Fourier transform, so we implicitly ruled them out when we took the Fourier transform of our differential equation.
::::::

As {prf:ref}`Ex:Fouriertr:Diffhom` shows, it is, in practice, only possible to find particular solutions using the Fourier transform and not the general solution. Fortunately, solving homogeneous equations is easier in general than finding particular solutions, so this is not a very big problem, but it is something to keep in mind.

::::::{prf:example} 
:label: Ex:Fouriertr:Diffdelta
Consider the differential equation

$$
 y''+2y'+5y=\delta(t),
$$

[^FootnoteNegt]: Of course, in practical situations, a system starts at some point in time, so considering negative values of $t$ is not necessary in those cases.

defined for **all** values of $t$. If we were to only consider positive values of $t$, we could use the Laplace transform, but that does not work when we consider all values of $t$.[^FootnoteNegt]

The physical interpretation of having a delta function as nonhomogeneous term, would be that we consider a mass-spring system where we hit the mass at precisely time zero.

We now take the Fourier transform of both sides of the equation to obtain

$$
 (i\omega)^2+2(i\omega)\hat{y}+5\hat{y}=1,
$$

which gives

$$
 \hat{y}=\frac{1}{-\omega^2+2i\omega+5}.
$$

In order to transform back, we need to write the right-hand side of this equation in terms of known Fourier transforms. For this, we make a partial fraction decomposition of the right-hand side. We notice that 

$$
 -\omega^2+2i\omega+5=-(\omega+(2-i))(\omega-(2+i)).
$$

Then we write

$$
 \frac{1}{-\omega^2+2i\omega+5}=\frac{A}{\omega+(2-i)}+\frac{B}{\omega-(2+i)}.
$$

Solving for $A$ and $B$ gives $A=\dfrac{1}{4}$ and $B=-\dfrac{1}{4}$, so we find

$$
 \hat{y}=\frac{1}{4}\frac{1}{\omega+(2-i)}-\frac{1}{4}\frac{1}{\omega-(2+i)}.
$$

These functions most closely resemble the ones from {prf:ref}`Ex:Fouriertr:Exponential`. Fortunately, we allowed $a$ to be a complex number in the example (at least one with positive real part), so we can use the computation from that example. Indeed, we can multiply the numerators and denominators of both fractions by $i$ to write

$$
 \hat{y}=\frac{i}{4}\frac{1}{i\omega+1+2i}-\frac{i}{4}\frac{1}{\omega+1-2i}.
$$

This is in the same form as the Fourier transform in {prf:ref}`Ex:Fouriertr:Exponential`, so we find that a particular solution $y_p(t)$ of this differential equation is given by

$$
 y_p(t)=\frac{i}{4}e^{-(1+2i)t}u_0(t)-\frac{i}{4}e^{-(1-2i)t}u_0(t)=\frac{1}{2}e^{-t}\left(\frac{e^{2it}-e^{-2it}}{2i}\right)u_0(t)=\frac{1}{2}e^{-t}\sin(2t)u_0(t).
$$

You can verify yourself that this solution satisfies the differential equation on the intervals $(-\infty,0)$ and $(0,\infty)$. At the point $t=0$ this is harder, since the derivative is discontinuous there (do note that the solution itself is continuous at $0$). If you want to formulate this properly mathematically you need to study the mathematical theory of distributions.

:::{figure} Images/Fig-FourierTrs-Diffdelta.png
:name: Fig:FourierTrs:Diffdelta

The graph of the particular solution $y_p(t)$ (left) and of its derivative (right).
:::

::::::

::::::{prf:example} 
:label: Ex:Fouriertr:Diffconv
Consider the differential equation

$$
 y''+4y'+29y=f(t)
$$

for some nonhomogenous term $f(t)$. Taking the Fourier transform of this equation, we obtain

$$
 (i\omega)^2+4i\omega\hat{y}+29\hat{y}=\hat{f}.
$$

Solving for $\hat{y}$ gives

$$
 \hat{y}=\hat{f}\frac{1}{(i\omega)^2+4i\omega +20}.
$$

Since $\hat{y}$ is the product of two functions, {prf:ref}`Thm:Fouriertr:Conv` tells us that

$$
 y=f\ast\mathcal{F}{-1}\left(\frac{1}{(i\omega)^2+4i\omega +20}\right).
$$

So the solution to this differential equation is always a convolution product of the nonhomogenous term and the same function $\mathcal{F}{-1}\left(\frac{1}{(i\omega)^2+4i\omega +20}\right)$. We can use this to our advantage in the following way: suppose we now choose $f(t)=\delta(t)$. Then we know that $\hat{f}(t)=1$, so in that case we obtain

$$
 \hat{y}=\frac{1}{(i\omega)^2+4i\omega +20},
$$

which gives

$$
 \mathcal{F}{-1}\left(\frac{1}{(i\omega)^2+4i\omega +20}\right).
$$

This means that this special function $\mathcal{F}{-1}\left(\frac{1}{(i\omega)^2+4i\omega +20}\right)$ is a particular solution to the differential equation with $f(t)=\delta(t)$. 

So if we know this solution (for instance, because we can measure it), we can use it to find the solution when we have a different $f$. It gets even better: this even works if we do not know the differential equation. As long as we can measure the reaction of the system when using the delta function as an external input, we can use the result to determine the reaction of the system to any other external input. We will make this idea precise in the theorem below.

::::::

::::::{prf:theorem} 
:label: Thm:Fouriertr:Diffconv
Consider the linear differential equation

$$
 \sum_n c_ny^{(n)}=\delta(t)
$$

where the $c_n$ are constants. Suppose $y_\delta$ is a solution to this differential equation. Then $y_p=f\ast y\delta$ is a particular solution to the equation

$$
 \sum_n c_ny^{(n)}=f(t).
$$
::::::



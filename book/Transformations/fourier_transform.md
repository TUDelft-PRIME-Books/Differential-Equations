::::{admonition} Attribution
:class: attribution
This page reuses content from {cite:t}`vdBult2025fouriertransform`.
::::


# Fourier transform

(Subsec:Fouriertr:Intro)=

## Introduction

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

So we can think of the Laplace transform as a Fourier transform with an *imaginary* input $\omega$ (we used $\omega=-is$ here). We will see that many properties of the two transformations work very similarly. The advantage of the Laplace transform is that it converges for more functions than the Fourier transform does. On the other hand, the inverse formula for the Laplace transform is too hard to work with, while for the Fourier transform we have an explicit expression (though that one can still be hard to work with in practice).
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
Let $a>0$ and consider the function 

$$
 \displaystyle f(t)=e^{-at}u_0(t)=\left\{\begin{array}{ll}0&t<0,\\ e^{-at}&t\geq 0.\end{array}\right.
$$

Here $u_0(t)$ is the Heaviside function centered around $0$, so 

$$
 u_0(t)=\left\{\begin{array}{ll}0&t<0,\\ 1&t\geq 0.\end{array}\right.
$$

:::{figure} Images/Fig-FourierTrs-Exp.png
:name: Fig:FourierTrs:Exp

The graph of the function $f$.
:::

Since the improper integral $\displaystyle \int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt$ has two infinite limits, we should evaluate this improper integral by splitting it up. It is convenient to split it up in the part from $-\infty$ to $0$ and the part from $0$ to $\infty$, since the function $f$ behaves differently on these parts. We can evaluate the Fourier transform of $f$ directly from the definition and we obtain

$$
 \begin{align*}\hat{f}(\omega)=&\int_{-\infty}^\infty e^{-at}u_0(t)e^{-i\omega t}\,dt\\
 =&\int_{-\infty}^0 0\cdot e^{-i\omega t}\,dt+\int_{0}^\infty e^{-at}e^{-i\omega t}\,dt\\
 =&0+\lim_{b\rightarrow\infty}\int_{0}^b e^{-at-i\omega t}\,dt\\
 =&\lim_{b\rightarrow\infty}\left[\frac{1}{-a-i\omega}e^{-at-i\omega t}\right]_0^b\\
 =&\frac{1}{a+i\omega}.\end{align*}
$$

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

:::{figure} Images/Fig-FourierTrs-Triangle.png
:name: Fig:FourierTrs:triangleFT

The graph of the Fourier transform of the function $f$.
:::

::::::

## Properties of the Fourier transform

In order to construct the Fourier transforms of more complicated functions, it is essential to know some general properties of the Fourier transform. Many of these properties are similar to those of the Laplace transform. The first one is that taking the Fourier transform is a linear operation.

::::::{prf:theorem} Linearity
:label: Thm:Fouriertr:Linear
For functions $f(t)$ and $g(t)$ whose Fourier transforms exist and constants  $c_{1},\,c_{2} \in \mathbb{R}$, it holds that  

$$
 {\mathcal F}\left\{c_{1} f(t) + c_{2} g(t)\right\}(\omega)=c_{1}{\mathcal F}\left\{f(t)\right\}(\omega)
+ c_{2}{\mathcal F}\left\{g(t)\right\}(\omega).
$$


::::::

:::{admonition} Proof of {prf:ref}`Thm:Fouriertr:Linear`
:class: tudproof, dropdown
Since the integral is linear (even an improper one), we find for any $\omega$ that

$$
 \mathcal{F}(c_1f+c_2g)(\omega)=\int_{-\infty}^\infty (c_1f(t)+c_2g(t))e^{-i\omega t}\,dt=c_1\int_{-\infty}^\infty f(t)e^{-i\omega t}\,dt+c_2\int_{-\infty}^\infty g(t)\,dt=c_1\mathcal{F}(f)(\omega)+c_2\mathcal{F}(g)(\pomega).
$$

This yields ${\mathcal F}\left\{c_{1} f(t) + c_{2} g(t)\right\}(\omega=c_{1}{\mathcal F}\left\{f(t)\right\}(\omega)+c_{2}{\mathcal F}\left\{g(t)\right\}(\omega)$, as desired.
:::

In {prf:ref}`Thm:Fouriertr:InvFouriertr` we saw that the inverse Fourier transform is very similar to the Fourier transform itself. So what happens if we apply the Fourier transform twice in a row? Then we expect to obtain something that is similar, but probably not quite the same, as the original function. Indeed, we have the following result.

::::::{prf:theorem} Duality
:label: Thm:Fouriertr:Duality
For a function $f(t)$ whose Fourier transform exists, it holds that 

$$
 {\mathcal F}\left\{\mathcal{F}\{f\}(\omega)\right\}(t)={\mathcal F}\left\{\hat{f}(\omega)\right\}(t) =  \int_{-\infty}^\infty \hat{f}(\omega)e^{-it\omega}\,d\omega=2\pi f(-t).
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
 2\pi f(-t)=\int_{-\infty}^{\infty}\hat{f}(\omega)e^{i(-t)\omega}\,d\omega.
$$

Now we interchange the symbols $t$ and $\omega$ to obtain

$$
 2\pi f(-\omega)=\int_{-\infty}^{\infty}\hat{f}(t)e^{-i\omega t}\,dt.
$$

The latter expression is, by definition, equal to $\mathcal{F}(\hat{f})(t)$, so we have found

$$
 2\pi f(-\omega)=\mathcal{F}(\hat{f})(t).
$$

Interchanging the symbols $t$ an $\omega$ again, we obtain

$$
 2\pi f(-t)=\mathcal{F}(\hat{f})(\omega),
$$

as desired.
:::

Recall that the Fourier transform $\mathcal{F}(f)(\omega)$ is a measure of how much of a wave with angular frequency $\omega$ is contained in the signal $f$. Now if we consider the function $g(t)=f(2t)$, then the signal goes twice as fast. If we compare the graphs of $f$ and $g$, then we obtain the graph of $g$ by compressing the one of $f$ in the $t$-direction by a factor $2$. If the Fourier transform of $f$ has a peak at a certain value $\omega_0$, then the Fourier transform of $g$ will have a peak at $2\omega_0$. This suggests that the graph of the Fourier transform of $g$ will be obtained from the one of the Fourier transform of $f$ by *stretching* it by a factor $2$ in the $\omega$-direction. However, this not is the entire story, since the amplitude of the Fourier transform also changes. In fact, we obtain the following result.

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

The graphs of the function $\pi e^{-|t|}$$ and its Fourier transform.
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
 =&e^{-2i\omega}\frac{2\sin(a\omega)}{\omega}.\end{align*}
$$

::::::

::::::{prf:example} Shift in frequency domain
:label: Ex:Fouriertr:Shiftfreq
In {prf:ref}`Ex:Fouriertr:Exponential` we have seen that for the function $f(t)=u_0(t)e^{-t}$ we have

$$
 \hat{f}(\omega)=\frac{1}{1+i\omega}.
$$

Now we, instead, consider the function $g(t)=e^{2it-t}u_0(t)=e^{2it}f(t)$. According to {prf:ref}`Thm:Fouriertr:Shift`, we must have

$$
 \hat{g}(\omega)=\hat{f}(\omega-2).
$$

We could also have found this Fourier transform directly by evaluating

$$
 \begin{align*}\hat{g}(\omega)=&\int_{-\infty}^\infty e^{2it-t}u_0(t)e^{-i\omega t}\,dt\\
 =&\int_{-\infty}^0 0\cdot e^{-i\omega t}\,dt+\int_{0}^\infty e^{2it-t}e^{-i\omega t}\,dt\\
 =&0+\lim_{b\rightarrow\infty}\int_{0}^b e^{\left(2i-1-i\omega\right) t}\,dt\\
 =&\lim_{b\rightarrow\infty}\left[\frac{1}{2i-1-i\omega}e^{\left(2i-1-i\omega\right) t}\right]_0^b\\
 =&-\frac{1}{2i-1-i\omega}\\
 =&\frac{1}{1+i(\omega-2)}\\
 =&\hat{f}(\omega-2).\end{align*}
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
 {\mathcal F}\left\{f'(t)\right\}(\omega)=\int_{-\infty}^\infty f'(t)e^{-it\omega}\,dt=\left[f(t)e^{-it\omega}\right]_{t=-\infty}^\infty-\int_{-\infty}^\infty (-i\omega)f'(t)e^{-it\omega}\,dt.
$$

We observe that $\displaystyle \lim_{t\rightarrow\pm\infty}f(t)e^{it\omega}=0$, since $\displaystyle \lim_{t\rightarrow\pm\infty}f(t)=0$ and $\left|e^{it\omega}\right|=1$. Hence, we obtain


$$
 {\mathcal F}\left\{f'(t)\right\}(\omega)=\left[f(t)e^{-it\omega}\right]_{t=-\infty}^\infty-\int_{-\infty}^\infty (-i\omega)f'(t)e^{-it\omega}\,dt=0+i\omega \int_{-\infty}^\infty f'(t)e^{-it\omega}\,dt=i\omega \hat{f}(\omega).
$$
:::

This means that the sometimes rather complicated operation of differentiation is nothing more than a mere multiplication on the Fourier side. Reversely, differentiation on the Fourier side of things should also give a multiplication in the time domain on account of duality. Indeed, we obtain the followin result.

::::::{prf:theorem} Multiplication by $t$
:label: Thm:Fouriertr:Multt
For a function $f(t)$ for which the Fourier transform of $tf(t)$ exists, the Fourier transform $\hat{f}(\omega)$ is differentiable and we have

$$
 i\dfrac{d}{d\omega}\hat{f}(\omega)=\mathcal{F}\left\{tf(t)\right\}(\omega).
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

Upon taking the $-i$ to the other side of the equation and using that $\dfrac{1}{-i}=i, we obtain

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

for some constant $a$. Then we have

$$
 \hat{f}(\omega)=\int_{-\infty}^\infty e^{-t^2}e^{-i\omega t}\,dt.
$$

According to {prf:ref}`Thm:Fouriertr:Multt`, we have

$$
 \frac{d}{d\omega}\hat{f}(\omega)=\frac{1}{i}\int_{-\infty}^\infty te^{-at^2}e^{-i\omega t}\,dt.
$$

Using integration by parts, we find

$$
 \frac{d}{d\omega}\hat{f}(\omega)=\left[-\frac{1}{2a}e^{-at^2}e^{-i\omega t}\right]_{t=-\infty}^\infty-\frac{\omega}{2a}\int_{-\infty}^\infty e^{-t^2}e^{-i\omega t}\,dt=0-\frac{\omega}{2a}\hat{f}(\omega)
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


Note that the graph of $f(t)=e^{-at^2}$ is very narrow/spiked when $a$ is very large, while it is rather flat if $a$ is rather flat. As we would expect from {prf:ref}`Thm:Fouriertr:Scaling`, this relation is inverted for the Fourier transform.[FootnoteUncertainty]

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

In order to make connect the function $g$ to this known Fourier transform, we perform a partial fraction decomposition. For this we note that $3+2i\omega+\omega^2=(\omega-i)(\omega+3i)$, so we write

$$
 \hat{g}(\omega)=\frac{1}{3+2i\omega+\omega^2}=\frac{A}{\omega-i}+\frac{B}{\omega+3i}.
$$

Solving for $A$ and $B$, we find $A=\dfrac{-i}{4}$ and $B=\dfrac{i}{4}$, so we have

$$
 \hat{g}(\omega)=\dfrac{-i}{4}\frac{1}{\omega-i}+\dfrac{i}{4}\frac{1}{\omega+3i}.
$$

To let it more closely resemble $\dfrac{1}{1+i\omega}$, we write

$$
 \hat{g}(\omega)=\dfrac{-i}{4}\frac{\frac{i}{2}}{i\frac{\omega}{2}+1}+\dfrac{i}{4}\frac{\frac{i}{-3}}{i\frac{\omega}{-3}+1}=\frac{1}{4}\frac{1}{2}\frac{1}{i\frac{\omega}{2}+1}+\frac{1}{4}\frac{1}{3}\frac{1}{i\frac{\omega}{-3}+1}.
$$

Now we note that

$$
 \frac{1}{2}\frac{1}{i\frac{\omega}{2}+1}=\frac{1}{2}\hat{f}\left(\frac{\omega}{2}\right)
$$

and

$$
 \frac{1}{3}\frac{1}{i\frac{\omega}{-3}+1}=\frac{1}{|-3|}\hat{f}\left(\frac{\omega}{-3}\right).
$$

As such, we have

$$
 g(\omega)=\frac{1}{4}\frac{1}{2}\hat{f}\left(\frac{\omega}{2}\right)+\frac{1}{4}\frac{1}{|-3|}\hat{f}\left(\frac{\omega}{-3}\right).
$$

Hence, with use {prf:ref}`Thm:Fouriertr:Scaling` we obtain that the inverse Fourier transform $g$ of $\hat{g}$ is given by

$$
 g(t)=\frac{1}{4} f(2t)+\frac{1}{4}f(-3t)=\frac{1}{4}e^{-2t}u_0(2t)+\frac{1}{4}e^{3t}u_0(-3t)=\left\{\begin{array}{ll}\frac{1}{4}e^{3t},\quad &t<0;\\[0.4cm] \frac{1}{4}e^{-t},\quad&t\geq 0.\end{array}\right.
$$

::::::

:::{todo}
Er moet nog
- Tabel met Fourier transforms
- Delta functies
- Convolutie
- Parseval/Plancherel (naamgeving checken, ook in slides)
- DVs oplossen
- INLEIDING

Zorg ook dat je bestand van meeting nog checkt.
:::

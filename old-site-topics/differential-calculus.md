---
title: Differential Calculus*
permalink: /old-site-topics/differential-calculus
parent: Old Site Topics*
nav_order: 3
---

# Differential Calculus

Suppose I want to talk about the rate of change of a function $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ without having to deal with averages. That is, rather than the average rate of change, I'd like to find the *instantaneous* rate of change of $$f$$, for which all I need to specify is a single $$x \in X$$ instead of an interval $$[a,b] \subseteq X$$. In my head, I'm picturing functions like [$$x \longmapsto x^3 - x \; \forall x \in \mathbb{R}$$](https://www.desmos.com/calculator/exv58lslxb): "Well-behaved" ones (we'll formalize what we mean by that). That's fine, because we can only do differential calculus (which revolves around this idea of an instantaneous rate of change) with ones that are "well-behaved," but it's important to keep in mind that not all functions are going to be kind enough to allow us to assign them an instantaneous rate of change (something crazy like [the Dirichlet function](https://en.wikipedia.org/wiki/Dirichlet_function), for example, is definitely not "well-behaved" in this sense, but is still a function).

To define this instantaneous rate of change, let's follow our intuition. If I placed a Desmos graph of a "well-behaved" function in front of you and asked you to tell me its slope at a particular point, you would look at the "trajectory" of that graph in the immediate vicinity of that point. In other words, your procedure would be to zoom in on the point so far that the graph looks like a line and then take the slope of that line (a line's rate of change never varies, so its instantaneous rate of change is its average rate of change over any interval). More formally: Take the slope of the graph in the limit as the range of input values we're looking at shrinks to zero and you'll get the graph's instantaneous rate of change, which we call its *derivative*.

## Definition: Derivative

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then the derivative of $$f(x)$$ *with respect to* $$x$$ is defined as

$$\frac{d(f(x))}{dx} \coloneqq \frac{df}{dx} \coloneqq \frac{d}{dx} f(x) \coloneqq \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}.$$

---

We use the notation $$\frac{df}{dx}$$ because often, finite changes in a quantity are denoted with a $$\Delta$$ prefix, so that the average rate of change of $$f(x)$$ with respect to $$x$$ can be written as $$\frac{\Delta f}{\Delta x}$$, and thus 

$$\frac{df}{dx} = \lim_{\Delta x \to 0} \frac{\Delta f}{\Delta x},$$

so $$d$$ is used to represent an "infinitesimal" version of $$\Delta.$$

We call the act of *taking a derivative* (i.e., going from $$f$$ to $$\frac{df}{dx}$$) *differentiation*, and since we can now see that being "well-behaved" just amounts to having a well-defined derivative, we call such a "well-behaved" function *differentiable*.

## Definition: Differentiable

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then $$f$$ is called differentiable at $$a$$ (and $$f(x)$$ is called differentiable with respect to $$x$$ at $$a$$) iff the derivative of $$f(x)$$ with respect to $$x$$ is well-defined for $$x = a$$, i.e.,

$$\lim_{\Delta x \to 0} \frac{f(a + \Delta x) - f(a)}{\Delta x}$$

exists.

---

But why 

$$\lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}$$

instead of, say, 

$$\lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x - \Delta x)}{2 \Delta x}?$$

Wouldn't that get us the same thing? And that second limit seems "nicer" in a way, since it's symmetric about $$x.$$ Here's why we use the particular limit that we do: We'd like to need that $$f$$ be well-defined for its derivative to exist. If $$f(x)$$ is not part of the definition of $$\frac{df}{dx}$$, we can't necessarily guarantee that $$\frac{df}{dx}$$ exists $$\implies f(x)$$ exists.

Requiring that $$f(x)$$ be part of the limit already leaves us only one option, but the nice thing is that this option also includes the requirement that $$f$$ be continuous at $$x$$, which we would also have wanted to require had we needed to.

## Theorem: Differentiable Implies Continuous

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$. Then if $$f$$ is differentiable at $$x$$, $$f$$ is continuous at $$x$$.

**Proof.** Assume that $$\frac{df}{dx}$$ exists (i.e., $$f$$ is differentiable at $$x$$). Then

$$\lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x} \lim_{\Delta x \to 0} \Delta x = \lim_{\Delta x \to 0} f(x + \Delta x) - f(x) = 0 \implies \lim_{\Delta x \to 0} f(x + \Delta x) = f(x) \Longleftrightarrow \lim_{y \to x} f(y) = f(x).$$

$$f$$ is continuous at $$x$$ by [Definition: Continuous](/limits#definition-continuous). $$\Box$$

---

Having now fully justified our definition, we can go on to prove a number of results about the derivative. Among the most intuitive of these is that if a function is differentiable at a local *extremum* (a local minimum or maximum), then its derivative must be $$0$$ there (otherwise nearby there would be a lower or higher value).

## Fermat's Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$. Suppose $$f(x_0)$$ is a local extremum of $$f$$ $$\exists x_0 \in X$$, i.e., 

$$\exists \delta > 0 \mid f(x) \geq f(x_0) \text{ or } f(x) \leq f(x_0) \; \forall x \in (x_0 - \delta, x_0 + \delta) \subseteq X.$$

Then if $$f$$ is differentiable at $$x_0$$,

$$\left.\frac{df}{dx}\right\rvert_{x_0} = 0.$$

**Proof.** Consider first the case where $$f(x_0)$$ is a local minimum of $$f$$. Then

$$\exists \delta > 0 \mid f(x) \geq f(x_0) \; \forall x \in (x_0 - \delta, x_0 + \delta) \subseteq X.$$

This means

$$\lim_{\Delta x \to 0^+} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} \geq 0,$$

$$\lim_{\Delta x \to 0^-} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} \leq 0.$$

Therefore if $$f$$ is differentiable at $$x_0$$,

$$\lim_{\Delta x \to 0^-} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} = \lim_{\Delta x \to 0^+} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} = \left.\frac{df}{dx}\right\rvert_{x_0} = 0.$$

An analogous argument applies for the case where $$f(x_0)$$ is a local maximum of $$f$$. $$\Box$$

---

It's also easy enough to intuit that if a function is differentiable on an interval, then at some point on that interval its instantaneous rate of change must be the same as its average rate of change (e.g., if you're driving a car at an average of sixty miles per hour, maybe at some point you're going faster than sixty and at some point you're going slower than sixty, but at some point you're going exactly sixty). We'll prove this in two steps: First a special case, then the general case.

## Rolle's Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then if $$f$$ is continuous from the right at $$a$$, continuous from the left at $$b$$, and differentiable on $$(a,b)$$ $$\exists a,b \in \mathbb{R}$$ and $$f(a) = f(b) = 0$$, then 

$$\exists c \in (a,b) \mid \left.\frac{df}{dx}\right\rvert_c = 0.$$

**Proof.** The case where $$f(x) = 0 \; \forall x \in [a,b]$$ is trivial. If $$f(x)$$ is nonzero $$\exists x \in [a,b]$$ then (noting that $$f$$ is continuous on $$(a,b)$$ by [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous)) by the [Extreme Value Theorem](/limits#extreme-value-theorem), $$f$$ attains a maximum and a minimum value on $$[a,b]$$, at least one of which is nonzero and thus occurs at some $$c \in (a,b)$$, where we then have 

$$\left.\frac{df}{dx}\right\rvert_c = 0$$

by [Fermat's Theorem](/differential-calculus#fermats-theorem). $$\Box$$

## Mean Value Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ If $$f$$ is continuous from the right at $$a$$, continuous from the left at $$b$$, and differentiable on $$(a,b)$$ $$\exists a,b \in \mathbb{R}$$ then 

$$\exists c \in (a,b) \mid \left.\frac{df}{dx}\right\rvert_c = \frac{f(b) - f(a)}{b - a}.$$

**Proof.** Let

$$D(x) = f(x) - \left[\frac{f(b) - f(a)}{b - a}(x - a) + f(a)\right].$$

$$D(x)$$ is continuous from the right at $$a$$, continuous from the left at $$b$$, and differentiable with respect to $$x$$ on $$(a,b)$$, and $$D(a) = D(b) = 0$$. Therefore, by [Rolle's Theorem](/differential-calculus#rolles-theorem),

$$\exists c \in (a,b) \mid \left.\frac{d(D(x))}{dx}\right\rvert_c = \left.\frac{df}{dx}\right\rvert_c - \frac{f(b) - f(a)}{b - a} = 0 \implies \left.\frac{df}{dx}\right\rvert_c = \frac{f(b) - f(a)}{b - a}. \text{ } \Box$$

---

We can also intuit the fact that

$$\frac{\text{Change in } f(x)}{\text{Change in } g(x)} = \frac{\frac{\text{Change in } f(x)}{\text{Change in } x}}{\frac{\text{Change in } g(x)}{\text{Change in } x}}$$

and thus arrive at the following kind of mean value theorem as well:

$$\frac{\left.\frac{df}{dx}\right\rvert_c}{\left.\frac{dg}{dx}\right\rvert_c} = \frac{f(b) - f(a)}{g(b) - g(a)} \; \exists c \in (a,b),$$

which we prove in a slightly altered form below to avoid any fussy issues involving division by zero.

## Cauchy's Mean Value Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ If $$f$$ and $$g$$ are continuous from the right at $$a$$, continuous from the left at $$b$$, and differentiable on $$(a,b)$$ $$\exists a,b \in \mathbb{R}$$ then 

$$\exists c \in (a,b) \mid [f(b) - f(a)]\left.\frac{dg}{dx}\right\rvert_c = [g(b) - g(a)]\left.\frac{df}{dx}\right\rvert_c.$$

**Proof.** Let

$$h(x) = [g(b) - g(a)]f(x) - [f(b) - f(a)]g(x).$$

Then $$h(a) = h(b)$$ and $$h$$ is continuous from the right at $$a$$, continuous from the left at $$b$$, and differentiable on $$(a,b)$$. Thus, by the [Mean Value Theorem](/differential-calculus#mean-value-theorem), 

$$\exists c \in (a,b) \mid \left.\frac{d(h(x))}{dx}\right\rvert_c = [g(b) - g(a)]\left.\frac{df}{dx}\right\rvert_c - [f(b) - f(a)]\left.\frac{dg}{dx}\right\rvert_c = 0 \implies [f(b) - f(a)]\left.\frac{dg}{dx}\right\rvert_c = [g(b) - g(a)]\left.\frac{df}{dx}\right\rvert_c. \text{ } \Box$$

---

This allows us to show the following result, which should make some sense as if $$f$$ and $$g$$ are two functions which start at zero somewhere,

$$\frac{f(x)}{g(x)} = \frac{\text{Change in } f(x)}{\text{Change in } g(x)} = \frac{\frac{\text{Change in } f(x)}{\text{Change in } x}}{\frac{\text{Change in } g(x)}{\text{Change in } x}}.$$

## Theorem: L'Hôpital's Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ If $$f$$ and $$g$$ are differentiable at $$x$$ $$\forall x \in (a - \delta, a + \delta)$$ $$\exists \delta > 0, a \in \mathbb{R}$$, $$\underset{x \to a}{\lim} f(x) = 0 = \underset{x \to a}{\lim} g(x)$$, and $$\underset{x \to a}{\lim} \frac{f(x)}{g(x)}$$ and $$\underset{x \to a}{\lim} \frac{\frac{df}{dx}}{\frac{dg}{dx}}$$ exist then 

$$\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{\frac{df}{dx}}{\frac{dg}{dx}}.$$

**Proof.** By [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous),

$$f(a) = 0 = g(a).$$

Let $$x \in (a, a + \delta) \mid g(y), \left.\frac{dg}{dx}\right\rvert_y \neq 0 \; \forall y \in (a,x)$$. (This must be possible because both limits exist.) Then by [Cauchy's Mean Value Theorem](/differential-calculus#cauchys-mean-value-theorem), 

$$\exists c \in (a, x) \mid f(x)\left.\frac{dg}{dx}\right\rvert_c = g(x)\left.\frac{df}{dx}\right\rvert_c \implies \frac{f(x)}{g(x)} = \frac{\left.\frac{df}{dx}\right\rvert_c}{\left.\frac{dg}{dx}\right\rvert_c} \implies \lim_{x \to a^+} \frac{f(x)}{g(x)} = \lim_{x \to a^+} \frac{\left.\frac{df}{dx}\right\rvert_c}{\left.\frac{dg}{dx}\right\rvert_c} = \lim_{c \to a^+} \frac{\left.\frac{df}{dx}\right\rvert_c}{\left.\frac{dg}{dx}\right\rvert_c} = \lim_{x \to a^+} \frac{\frac{df}{dx}}{\frac{dg}{dx}}.$$

A similar argument applies for approaching from the left, and thus we must have

$$\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{\frac{df}{dx}}{\frac{dg}{dx}}. \text{ } \Box$$

---

Now we proceed to derive formulas to streamline the process of differentiating various classes of function. These first four should hopefully be very intuitive:

## Theorem: Constant Rule

Let $$c \in \mathbb{R}$$. Then

$$\frac{dc}{dx} = 0.$$

**Proof.** By [Definition: Derivative](/differential-calculus#definition-derivative),

$$\frac{dc}{dx} = \lim_{\Delta x \to 0} \frac{c - c}{\Delta x} = 0. \text{ } \Box$$

---

(Constants don't change, so their rate of change is zero.)

## Theorem: Sum Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$x$$. Then

$$\frac{d(f \pm g)}{dx} = \frac{df}{dx} \pm \frac{dg}{dx}.$$

**Proof.** By [Definition: Derivative](/differential-calculus#definition-derivative), 

$$\frac{df}{dx} \pm \frac{dg}{dx} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}  \pm \lim_{\Delta x \to 0} \frac{g(x + \Delta x) - g(x)}{\Delta x} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) \pm g(x + \Delta x) - f(x) \mp g(x)}{\Delta x} = \frac{d(f \pm g)}{dx}. \text{ } \Box$$

---

(The total increase of a function equals the sum of its terms' increases, so total increase per change in $$x$$ equals sum of increases per change in $$x$$.)

## Theorem: Constant Factor Rule

Let $$c \in \mathbb{R}$$. Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$x$$. Then

$$\frac{d(cf)}{dx} = c \frac{df}{dx}.$$

**Proof.** By [Definition: Derivative](/differential-calculus#definition-derivative),

$$c \frac{df}{dx} = c \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x} = \lim_{\Delta x \to 0} \frac{cf(x + \Delta x) - cf(x)}{\Delta x} = \frac{d(cf)}{dx}. \text{ } \Box$$

---

(A scale factor of $$c$$ essentially stretches the function out by a factor of $$c$$, so the function's slope stretches out by $$c$$ as well.)

## Theorem: Derivative With Respect to Self

$$\frac{dx}{dx} = 1.$$

**Proof.** By [Definition: Derivative](/differential-calculus#definition-derivative),

$$\frac{dx}{dx} = \lim_{\Delta x \to 0} \frac{x + \Delta x - x}{\Delta x} = \lim_{\Delta x \to 0} \frac{\Delta x}{\Delta x} = 1. \text{ } \Box$$

---

(The ratio of change in $$x$$ to change in $$x$$ is $$1$$.)

This last result suggests a different kind of intuition about the derivative: that we should expect it to behave very much like a fraction as it is essentially a ratio of "infinitesimal" changes. This means we might expect that

$$\frac{df}{dg} \cdot \frac{dg}{dx} = \frac{df}{dx}$$

as if the derivative were truly a fraction, the $$dg$$s would "cancel." 

There are two small problems with this intuition. The first is that it won't be a change in $$f$$ alone that ends up in the "numerator" as 

$$\frac{df}{dg} = \frac{d(f(g))}{dg},$$

so what we'll really end up with is $$\frac{d(f \circ g)}{dx}$$.

Secondly, we can't forget that we're going to have an issue if $$dg = 0$$. We're fine in every other case as, loosely speaking, on this scale (having zoomed in infinitely far so that the graph looks perfectly linear for any finite amount of zooming out we do), whether $$g$$ changes by one "infinitesimal" increment or two is completely irrelevant as far as the ratio $$\frac{df}{dg}$$ is concerned and so we can always take the two $$dg$$s to be the same and thus "cancel" them, but if $$dg = 0$$, we won't be able to. Luckily, this is precisely the case where we don't need to; the whole thing will multiply to zero:

$$\frac{d(f(g))}{dg} \cdot \frac{dg}{dx} = \frac{d(f(g))}{dg} \cdot \frac{0}{dx} = 0,$$

which is exactly what we expect to be the value of $$\frac{d(f \circ g)}{dx}$$ (if $$g$$ isn't changing, $$f \circ g$$ can't be either). So it still works out. Here it is all together and with much less shaky reasoning.

## Theorem: Chain Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$g(x)$$ with $$g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ differentiable at $$x$$. Then

$$\frac{d(f \circ g)}{dx} = \left.\frac{df}{dg}\right\rvert_{g(x)} \frac{dg}{dx}.$$

**Proof.** Let

$$Q(\Delta x) = \begin{cases} \frac{f(g(x + \Delta x)) - f(g(x))}{g(x + \Delta x) - g(x)} & g(x + \Delta x) - g(x) \neq 0 \\ \left.\frac{df}{dg}\right\rvert_{g(x)} & g(x + \Delta x) - g(x) = 0 \end{cases}.$$

$$Q(\Delta x) \cdot \frac{g(x + \Delta x) - g(x)}{\Delta x} = \frac{f(g(x + \Delta x)) - f(g(x))}{\Delta x} \; \forall \Delta x \in \mathbb{R}.$$

$$\lim_{\Delta x \to 0} Q(\Delta x) = \left.\frac{df}{dg}\right\rvert_{g(x)}$$

by [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous). Therefore

$$\frac{d(f \circ g)}{dx} = \lim_{\Delta x \to 0} \frac{f(g(x + \Delta x)) - f(g(x))}{\Delta x} = \lim_{\Delta x \to 0} Q(\Delta x) \cdot \frac{g(x + \Delta x) - g(x)}{\Delta x} = \lim_{\Delta x \to 0} Q(\Delta x) \cdot \lim_{\Delta x \to 0} \frac{g(x + \Delta x) - g(x)}{\Delta x} = \left.\frac{df}{dg}\right\rvert_{g(x)} \frac{dg}{dx}. \text{ } \Box$$

---

We would similarly expect that 

$$\frac{dx}{dy} = \frac{1}{\frac{dy}{dx}}.$$

## Theorem: Inverse Function Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$x$$ with $$\frac{df}{dx} \neq 0$$ and injective on $$(a,b)$$ $$\exists x \in (a,b) \subseteq X, a, b \in \mathbb{R}$$ with $$f^{-1}$$ its inverse on $$(a,b)$$. Then

$$\left.\frac{df^{-1}}{dy}\right\rvert_{f(x)} = \frac{1}{\frac{df}{dx}}.$$

**Proof.** Because $$f$$ is invertible on $$(a,b)$$, every $$f(x) + \Delta y$$ in the domain of $$f^{-1}$$ has a unique $$\Delta x \mid f(x + \Delta x) = f(x) + \Delta y$$. Therefore

$$\left.\frac{df^{-1}}{dy}\right\rvert_{f(x)} = \lim_{\Delta y \to 0} \frac{f^{-1}(f(x) + \Delta y) - f^{-1}(f(x))}{\Delta y} = \lim_{\Delta x \to 0} \frac{f^{-1}(f(x + \Delta x)) - f^{-1}(f(x))}{f(x + \Delta x) - f(x)} = \lim_{\Delta x \to 0} \frac{\Delta x}{f(x + \Delta x) - f(x)} = \lim_{\Delta x \to 0} \frac{1}{\frac{f(x + \Delta x) - f(x)}{\Delta x}} = \frac{1}{\underset{\Delta x \to 0}{\lim} \frac{f(x + \Delta x) - f(x)}{\Delta x}} = \frac{1}{\frac{df}{dx}}$$

since $$\Delta x \to 0 \implies \Delta y \to 0$$ by [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous). $$\Box$$

---

Now let's consider some common types of functions and see if they're differentiable and if we can find some formulas for their derivatives. We'll start with exponentials.

## Theorem: Derivative of Exponential

Let $$a \in \mathbb{R} > 0$$. Then $$a^x$$ is differentiable with respect to $$x$$ $$\forall x \in \mathbb{R}$$.

**Proof.**

$$\frac{d(a^x)}{dx} = \lim_{\Delta x \to 0} \frac{a^{x + \Delta x} - a^x}{\Delta x} = a^x \cdot \lim_{\Delta x \to 0} \frac{a^{\Delta x} - 1}{\Delta x}.$$

It remains to be shown that this last limit exists. Note firstly that this is trivial if $$a = 1$$, and start by considering the $$a > 1$$ case.

Let $$r \in \mathbb{Z} > 0$$. Then 

$$ra^r = \underbrace{a^r + \cdots + a^r}_{r \text{ terms}} > a^{r - 1} + a^{r - 2} + \cdots + 1 \implies ra^r(a - 1) > a^r - 1$$

after multiplying both sides of the inequality by $$a - 1$$. Add $$r(a^r - 1)$$ to both sides:

$$r(a^{r + 1} - 1) > (r + 1)(a^r - 1) \implies \frac{a^{r + 1} - 1}{r + 1} > \frac{a^r - 1}{r}.$$

Thus, where $$s \in \mathbb{Z} > r$$, 

$$\frac{a^{s} - 1}{s} > \frac{a^r - 1}{r}.$$

Now, let $$t, u, v, w \in \mathbb{Z} > 0, r = \frac{t}{u}, s = \frac{v}{w}, \gamma = a^{\frac{1}{uw}}.$$ Note that

$$s > r \Longleftrightarrow vu > tw,$$

$$\gamma > 1.$$

Therefore

$$\frac{\gamma^{vu} - 1}{vu} > \frac{\gamma^{tw} - 1}{tw} \implies \frac{a^\frac{v}{w} - 1}{vu} > \frac{a^\frac{t}{u} - 1}{tw} \implies \frac{a^{s} - 1}{s} > \frac{a^r - 1}{r}.$$

Since $$t, u, v, w$$ were arbitrary, this must hold $$\forall r, s \in \mathbb{Q} > 0 \mid s > r$$. Since $$\frac{a^{\Delta x} - 1}{\Delta x}$$ is continuous $$\forall \Delta x \in \mathbb{R} \neq 0$$, we have that $$\frac{a^{\Delta x} - 1}{\Delta x}$$ increases with $$\Delta x$$ on $$(0, \infty)$$. We also have that $$\frac{a^{\Delta x} - 1}{\Delta x} > 0 \; \forall \Delta x > 0$$. Thus,

$$\exists L \in \mathbb{R} \geq 0 \mid \forall \epsilon > 0 \; \exists \delta > 0 \mid \Delta x \in (0, \delta) \implies \frac{a^{\Delta x} - 1}{\Delta x} \in [L, L + \epsilon) \subset (L - \epsilon, L + \epsilon) \Longleftrightarrow \lim_{\Delta x \to 0^+} \frac{a^{\Delta x} - 1}{\Delta x} = L,$$

$$\lim_{\Delta x \to 0^-} \frac{a^{\Delta x} - 1}{\Delta x} = \lim_{\Delta x \to 0^+} \frac{a^{-\Delta x} - 1}{-\Delta x}= \lim_{\Delta x \to 0^+} \frac{a^{\Delta x} - 1}{a^{\Delta x}\Delta x} = \lim_{\Delta x \to 0^+} \frac{a^{\Delta x} - 1}{\Delta x} = L \implies \lim_{\Delta x \to 0} \frac{a^{\Delta x} - 1}{\Delta x} = L.$$

If $$a \in (0,1)$$, $$\exists b \in \mathbb{R} > 1 \mid a = \frac{1}{b}$$, and so

$$\lim_{\Delta x \to 0} \frac{a^{\Delta x} - 1}{\Delta x} = \lim_{\Delta x \to 0} \frac{b^{-\Delta x} - 1}{\Delta x} = \lim_{\Delta x \to 0} \frac{1 - b^{\Delta x}}{b^{\Delta x}\Delta x} = \lim_{\Delta x \to 0} \frac{1 - b^{\Delta x}}{\Delta x} = -\lim_{\Delta x \to 0} \frac{b^{\Delta x} - 1}{\Delta x}$$

exists. $$\Box$$

---

For reasons we'll uncover as we continue, this difficult limit we just spent so much time on is rather special. It's called the *natural logarithm* of $$a$$, and as we've seen, it's defined $$\forall a > 0$$.

## Definition: Natural Logarithm

$$\forall x > 0$$, the natural logarithm of $$x$$ is defined as

$$\ln(x) \coloneqq \lim_{h \to 0} \frac{x^h - 1}{h}.$$

(See [Derivative of Exponential](/differential-calculus#theorem-derivative-of-exponential) for a proof that $$\ln(x)$$ is well-defined.)

---

Therefore the derivative of $$a^x$$ with respect to $$x$$ can be more compactly written as $$a^x \ln a.$$

This brings up a curious possibility: If $$\exists e \in \mathbb{R} > 0 \mid \ln e = 1$$, we will have that $$e^x$$ is its own derivative with respect to $$x$$. To see if such a constant exists, let's discern a few properties of $$\ln$$. (You can arrive at educated guesses as to these properties by hoping that $$\ln$$ lives up to its name and is in fact the logarithm with base $$e$$.)

## Theorem: Natural Logarithm Power Property

Let $$x > 0, y \in \mathbb{R}$$. Then

$$\ln(x^y) = y \ln x.$$

**Proof.** If $$y \neq 0$$ then by [Definition: Natural Logarithm](/differential-calculus#definition-natural-logarithm),

$$\ln(x^y) = \lim_{h \to 0} \frac{x^{yh} - 1}{h} = y \cdot \lim_{yh \to 0} \frac{x^{yh} - 1}{yh} = y \ln x.$$

If $$y = 0$$ then by [Definition: Natural Logarithm](/differential-calculus#definition-natural-logarithm),

$$\ln(x^y) = \ln(1) = \lim_{h \to 0} \frac{1^h - 1}{h} = 0 = y \ln x. \text{ } \Box$$

## Theorem: Natural Logarithm Product Property

Let $$x, y > 0$$. Then

$$\ln(xy) = \ln x + \ln y.$$

**Proof.** By [Definition: Natural Logarithm](/differential-calculus#definition-natural-logarithm),

$$\ln(xy) = \lim_{h \to 0} \frac{(xy)^h - 1}{h} = \lim_{h \to 0} \frac{x^hy^h - 1}{h} = \lim_{h \to 0} \frac{x^hy^h + x^h + y^h - x^h - y^h - 1}{h} = \lim_{h \to 0} \frac{x^h - 1 + y^h - 1 + x^hy^h - x^h - y^h + 1}{h} = \lim_{h \to 0} \frac{x^h - 1 + y^h - 1 + (x^h - 1)(y^h - 1)}{h} = \lim_{h \to 0} \frac{x^h - 1}{h} + \lim_{h \to 0} \frac{y^h - 1}{h} + \lim_{h \to 0}(x^h - 1) \lim_{h \to 0} \frac{y^h - 1}{h} = \ln x + \ln y. \text{ } \Box$$

---

We don't actually need the second one for this, but we went ahead and proved it because it'll come in handy a little farther down the line. All we need apart from the first proof is the fact that $$\ln$$ is nonzero somewhere, which is extremely simple to see—If it were zero everywhere, we would have that $$a^x \mid a > 0, a \neq 1$$ never changes, which is obviously false. Thus, we've confirmed the existence of one of the coolest numbers known to man! It's simple enough to see that it's unique, too.

## Theorem: $$e$$ Exists

$$\exists! e \in \mathbb{R} > 0 \mid \ln e = 1.$$

**Proof.** Let $$a, x \in \mathbb{R} \mid a \neq 1, a > 0$$. Since $$a^x$$ is differentiable and monotonous with respect to $$x$$ and

$$\left.\frac{d(a^x)}{dx}\right\rvert_0 = \ln a,$$

we must have that $$\ln a \neq 0$$. Therefore, by [Natural Logarithm Power Property](/differential-calculus#theorem-natural-logarithm-power-property),

$$\ln(a^x) = x \ln a = 1$$

must be possible. Furthermore, because $$x \ln a = \ln(a^x), a^x$$ are both monotonous and continuous with respect to $$x$$ and the range of $$a^x$$ is equal to the domain of $$\ln$$, we must have that $$\ln$$ is monotonous and continuous and thus 

$$\exists! e \in \mathbb{R} > 0 \mid \ln e = 1. \text{ } \Box$$

## Definition: $$e$$

$$e$$ is defined as the unique real constant greater than zero such that

$$\ln e = 1.$$

(For a proof that this is possible, see [$$e$$ exists](/differential-calculus#theorem-e-exists).)

---

Now we can confirm that $$\ln$$ is indeed the logarithm with base $$e$$:

$$\ln(e^x) = x \ln e = x \; \forall x \in \mathbb{R},$$

and similarly,

$$\ln x = \ln x \cdot \ln e = \ln(e^{\ln x}) \implies x = e^{\ln x} \; \forall x > 0$$

since $$\ln$$ is monotonous. Therefore $$e^x$$ and $$\ln x$$ are inverses of each other, and so we know how to find the derivative of $$\ln$$.

## Theorem: Derivative of Natural Logarithm

$$\frac{d(\ln x)}{dx} = \frac{1}{x} \; \forall x > 0.$$

**Proof.** By [Natural Logarithm Power Property](/differential-calculus#theorem-natural-logarithm-power-property) and the definition of $$e$$,

$$\ln(e^x) = x \ln e = x \; \forall x \in \mathbb{R}.$$

Therefore $$\ln x$$ is the inverse of $$e^x$$, so by [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule) and the definition of $$e$$, 

$$\left.\frac{d(\ln y)}{dy}\right\rvert_{e^x} = \frac{1}{\frac{d(e^x)}{dx}} = \frac{1}{e^x} \implies \frac{d(\ln x)}{dx} = \frac{1}{e^{\ln x}} = \frac{1}{x} \; \forall x > 0. \text{ } \Box$$

---

It'll also be helpful that we notice the following.

## Theorem: Derivative of Natural Logarithm of Absolute Value

$$\frac{d(\ln \lvert x \rvert)}{dx} = \frac{1}{x} \; \forall x \in \mathbb{R}.$$

**Proof.** By the definition of the absolute value function,

$$\frac{d(\ln \lvert x \rvert)}{dx} = \frac{d}{dx} \begin{cases} \ln(-x) & x < 0 \\ \text{undefined} & x = 0 \\ \ln x & x > 0 \end{cases} = \begin{cases} \frac{1}{-x} \cdot -1 & x < 0 \\ \text{undefined} & x = 0 \\ \frac{1}{x} & x > 0 \end{cases} = \frac{1}{x} \; \forall x \in \mathbb{R}$$

by [Chain Rule](/differential-calculus#theorem-chain-rule) and [Derivative of Natural Logarithm](/differential-calculus#theorem-derivative-of-natural-logarithm). $$\Box$$

---

Now we're all set to really have some fun. Having established the key properties of $$\ln$$ and $$e$$, figuring out other derivative formulas will be a breeze, especially with the help of the chain rule.

## Theorem: Product Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$x$$. Then

$$\frac{d(f(x)g(x))}{dx} = \frac{df}{dx} g(x) + f(x) \frac{dg}{dx}.$$

**Proof.** Let $$y = f(x)g(x)$$. Then if $$f(x), g(x) \neq 0$$,

$$\ln \lvert y \rvert = \ln(\lvert f(x) \rvert) + \ln(\lvert g(x) \rvert) \implies \frac{1}{y} \frac{dy}{dx} = \frac{1}{f(x)g(x)} \frac{d(f(x)g(x))}{dx} = \frac{1}{f(x)} \frac{df}{dx} + \frac{1}{g(x)} \frac{dg}{dx} \implies \frac{d(f(x)g(x))}{dx} = \frac{df}{dx} g(x) + f(x) \frac{dg}{dx}$$

by [Derivative of Natural Logarithm of Absolute Value](/differential-calculus#theorem-derivative-of-natural-logarithm-of-absolute-value), [Chain Rule](/differential-calculus#theorem-chain-rule), [Natural Logarithm Product Property](/differential-calculus#theorem-natural-logarithm-product-property), and [Sum Rule](/differential-calculus#theorem-sum-rule). If $$f(x) = 0$$, 

$$\frac{d(f(x)g(x))}{dx} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x)g(x + \Delta x) - f(x)g(x)}{\Delta x} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x)g(x + \Delta x) - f(x)g(x + \Delta x)}{\Delta x} = \lim_{\Delta x \to 0} g(x + \Delta x) \lim_{\Delta x \to 0} \frac{f(x + \Delta x - f(x)}{\Delta x} = g(x) \frac{df}{dx} = \frac{df}{dx} g(x) + f(x) \frac{dg}{dx}$$

by [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous), and the same result holds by an analogous argument if $$g(x) = 0$$. $$\Box$$

## Theorem: Quotient Rule

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$x$$ with $$g(x) \neq 0$$. Then

$$\frac{d\left(\frac{f(x)}{g(x)}\right)}{dx} = \frac{g(x) \frac{df}{dx} - f(x) \frac{dg}{dx}}{g(x)^2}.$$

**Proof.** Let $$y = \frac{f(x)}{g(x)}$$. Then if $$f(x) \neq 0$$,

$$\ln \lvert y \rvert = \ln \lvert f(x) \rvert + \ln \lvert g(x)^{-1} \rvert = \ln \lvert f(x) \rvert - \ln \lvert g(x) \rvert \implies \frac{1}{y} \frac{dy}{dx} = \frac{g(x)}{f(x)} \frac{d\left(\frac{f(x)}{g(x)}\right)}{dx} = \frac{1}{f(x)} \frac{df}{dx} - \frac{1}{g(x)} \frac{dg}{dx} \implies \frac{d\left(\frac{f(x)}{g(x)}\right)}{dx} = \frac{1}{g(x)} \frac{df}{dx} - \frac{f(x)}{g(x)^2} \frac{dg}{dx} = \frac{g(x)\frac{df}{dx} - f(x) \frac{dg}{dx}}{g(x)^2}$$

by [Derivative of Natural Logarithm of Absolute Value](/differential-calculus#theorem-derivative-of-natural-logarithm-of-absolute-value), [Chain Rule](/differential-calculus#theorem-chain-rule), [Natural Logarithm Product Property](/differential-calculus#theorem-natural-logarithm-product-property), [Natural Logarithm Power Property](/differential-calculus#theorem-natural-logarithm-power-property), and [Sum Rule](/differential-calculus#theorem-sum-rule). If $$f(x) = 0$$,

$$\frac{d\left(\frac{f(x)}{g(x)}\right)}{dx} = \lim_{\Delta x \to 0} \frac{\frac{f(x + \Delta x)}{g(x + \Delta x)} - \frac{f(x)}{g(x)}}{\Delta x} = \lim_{\Delta x \to 0} \frac{\frac{f(x + \Delta x)}{g(x + \Delta x)} - \frac{f(x)}{g(x + \Delta x)}}{\Delta x} = \lim_{\Delta x \to 0} \frac{1}{g(x + \Delta x)} \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x} = \frac{1}{g(x)} \frac{df}{dx} = \frac{g(x) \frac{df}{dx} - f(x) \frac{dg}{dx}}{g(x)^2}$$

by [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous). $$\Box$$

## Theorem: Power Rule

Let $$n \in \mathbb{R}$$. Then where $$x \neq 0$$ or $$n \notin \{0, 1\}$$,

$$\frac{d(x^n)}{dx} = nx^{n - 1}.$$

**Proof.** Let $$y = x^n$$. Then where $$x \neq 0$$,

$$\ln \lvert y \rvert = \ln \lvert x^n \rvert = n \ln \lvert x \rvert \implies \frac{1}{y} \frac{dy}{dx} = \frac{1}{x^n} \frac{d(x^n)}{dx} = \frac{n}{x} \implies \frac{d(x^n)}{dx} = nx^{n - 1}$$

by [Derivative of Natural Logarithm of Absolute Value](/differential-calculus#theorem-derivative-of-natural-logarithm-of-absolute-value), [Chain Rule](/differential-calculus#theorem-chain-rule), [Natural Logarithm Power Property](/differential-calculus#theorem-natural-logarithm-power-property), and [Constant Factor Rule](/differential-calculus#theorem-constant-factor-rule). If $$x = 0$$,

$$\frac{d(x^n)}{dx} = \lim_{\Delta x \to 0} \frac{(x + \Delta x)^n - x^n}{\Delta x} = \lim_{\Delta x \to 0} (\Delta x)^{n - 1}.$$

If $$n < 1$$ then

$$\exists a > 0 \mid n - 1 = -a \implies (\Delta x)^{n - 1} = \frac{1}{(\Delta x)^a}$$

and the limit does not exist, nor does $$nx^{n-1}$$. If $$n > 1$$ then the limit is $$0 = nx^{n-1}$$ by continuity. $$\Box$$

## Theorem: Derivative of Logarithm

Let $$a > 0, a \neq 1$$. Then

$$\frac{d(\log_a(x))}{dx} = \frac{1}{x \ln a} \; \forall x > 0.$$

**Proof.** By [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule),

$$\left.\frac{d(\log_a(y))}{dy}\right\rvert_{a^x} = \frac{1}{\frac{d(a^x)}{dx}} = \frac{1}{a^x \ln a} \implies \frac{d(\log_a(x))}{dx} = \frac{1}{x \ln a} \; \forall x > 0. \text{ } \Box$$

---

And that's basically every common differentiation formula we can derive! (Unless you [buy the DLC](/trigonometry).)

Now let's return to the concept of differentiability for a moment. If you haven't picked up on this already, the quality of differentiability has a very natural layman's interpretation in the form of local linearity. That is, loosely speaking, a function is differentiable at a point iff it looks like a line if you zoom in far enough on that point. This means if we construct a line with slope $$\left.\frac{df}{dx}\right\rvert_a$$ that passes through the point $$(a, f(a))$$, it will be a decent approximation of $$f(x)$$ for $$x$$ near $$a$$. Such a line is called a *tangent line*.

## Definition: Tangent Line

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be differentiable at $$a$$. Then the tangent line to $$f$$ at $$a$$ is the function

$$x \longmapsto \left.\frac{df}{dx}\right\rvert_a (x - a) + f(a) \; \forall x \in \mathbb{R}.$$

---

For the sake of practice, I encourage you to use our derived differentiation formulas to find the tangent line to $$x \longmapsto x^3 - x \; \forall x \in \mathbb{R}$$ at any generic $$x$$-value $$a$$. Once you have, [here](https://www.desmos.com/calculator/qry0cruqps)'s a Desmos graph for you to play around with it and see what it looks like.

Now I'd like to ask you a question that might seem silly, but I want to make sure you think all the way through the answer: Why is a tangent line not a perfect approximation of a graph? Well, because in general, graphs' slopes change, right? One could even say they have nonzero rates of change. But wait a minute. We know how to quantify rates of change...

## Notation: Higher-Order Derivatives

For $$n \in \mathbb{Z} > 1$$, where $$f$$ is a function,

$$\frac{d^nf}{dx^n} \coloneqq \frac{d^n(f(x))}{dx^n} \coloneqq \frac{d^n}{dx^n} f(x)\coloneqq \underbrace{\frac{d}{dx} \cdots \frac{d}{dx}}_{n \text{ times}} f(x).$$

---

...if they exist, which they don't in general. But if they do, if a function is, say, *twice-differentiable*, that is, the derivative of its derivative exists, then maybe we can construct a tangent parabola to the function which is a better approximation of it. We choose parabolas because those have constant second derivatives, just like lines have constant first derivatives: Where $$a, b, c \in \mathbb{R}$$,

$$\frac{d^2}{dx^2}(ax^2 + bx + c) = \frac{d}{dx}(2ax + b) = 2a = \text{constant}$$

by [Sum Rule](/differential-calculus#theorem-sum-rule), [Power Rule](/differential-calculus#theorem-power-rule), [Derivative With Respect to Self](/differential-calculus#theorem-derivative-with-respect-to-self), [Constant Factor Rule](/differential-calculus#theorem-constant-factor-rule), and [Constant Rule](/differential-calculus#theorem-constant-rule). So, if we want to find the tangent quadratic to the function $$f$$ at $$0$$ where $$\left.\frac{d^2f}{dx^2}\right\rvert_0$$ is well-defined, we can set $$a = \frac{1}{2}\left.\frac{d^2f}{dx^2}\right\rvert_0$$, $$b = \left.\frac{df}{dx}\right\rvert_0$$, and $$c = f(0)$$ so that the parabola's first and second derivatives and value ("zeroeth derivative") all coincide with those of the function at $$0$$, and so

$$x \longmapsto ax^2 + bx + c = \frac{1}{2}\left.\frac{d^2f}{dx^2}\right\rvert_0 x^2 + \left.\frac{df}{dx}\right\rvert_0 x + f(0) \; \forall x \in \mathbb{R}$$

will be our tangent parabola to $$f$$ at $$0$$, and in general,

$$x \longmapsto \frac{1}{2}\left.\frac{d^2f}{dx^2}\right\rvert_{x_0} (x - x_0)^2 + \left.\frac{df}{dx}\right\rvert_{x_0} (x - x_0) + f(x_0) \; \forall x \in \mathbb{R}$$

will be our tangent parabola to $$f$$ at $$x_0$$. ([Here](https://www.desmos.com/calculator/grtf8r2esl)'s what that looks like for $$f \colon x \longmapsto x^3 - x \; \forall x \in \mathbb{R}$$.)

Of course, now we run into the same issue again: In general, functions are not parabolic; the rate of change of the rate of change of a function's rate of change is in general nonzero. And so then we could construct a tangent cubic

$$x \longmapsto \frac{1}{6} \left.\frac{d^3f}{dx^3}\right\rvert_{x_0} (x - x_0)^3 + \frac{1}{2}\left.\frac{d^2f}{dx^2}\right\rvert_{x_0} (x - x_0)^2 + \left.\frac{df}{dx}\right\rvert_{x_0} (x - x_0) + f(x_0) \; \forall x \in \mathbb{R}$$

($$\frac{1}{6}$$ being the leading coefficient because after differentiating three times we end up with $$3 \cdot 2 \cdot \frac{1}{6} \left.\frac{d^3f}{dx^3}\right\rvert_{x_0} = \left.\frac{d^3f}{dx^3}\right\rvert_{x_0}$$) to $$f$$ at $$x_0$$ (if $$f$$ will allow it) only to run into the same issue, and so on in a vicious cycle, but at least we can console ourselves with the fact that for the right class of function $$f$$, with each repetition of the cycle our approximation gets better. These polynomials, by the way, are called *Taylor polynomials*.

## Definition: Taylor Polynomial

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be $$n$$ times differentiable at $$x_0$$ for some $$n \in \mathbb{Z} \geq 1$$. Then the Taylor polynomial to $$f$$ at $$x_0$$ is defined to be the function

$$x \longmapsto \sum_{k = 1}^n \frac{1}{k!} \left.\frac{d^kf}{dx^k}\right\rvert_{x_0} (x - x_0)^k + f(x_0) \; \forall x \in \mathbb{R}.$$

---

(The $$\frac{1}{k!}$$ is there for the same reason as the $$\frac{1}{6}$$ in the $$n = 3$$ case.) Of course, now we've got to take the limit as $$n \longrightarrow \infty$$, turning the Taylor polynomial into a *Taylor series*, and see under what conditions we can get a perfect approximation. (Note that we don't always *have* to let $$n \longrightarrow \infty$$—E.g., any degree $$n$$ polynomial is its own degree $$n$$ Taylor polynomial—But all the interesting functions, being non-polynomials, will likely need this. Also note that an infinitely differentiable function is called *smooth*.)

## Definition: Smooth

A function $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ is called smooth at $$x$$ iff $$\frac{d^nf}{dx^n}$$ is well-defined $$\forall n \in \mathbb{Z} > 1$$.

## Definition: Taylor Series

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be smooth at $$x_0$$. Then the Taylor series to $$f$$ at $$x_0$$ is defined to be the function

$$x \longmapsto \sum_{k = 1}^{\infty} \frac{1}{k!} \left.\frac{d^kf}{dx^k}\right\rvert_{x_0} (x - x_0)^k + f(x_0) \; \forall x \in \mathbb{R}.$$

---

To best answer our question, we'll phrase it like this: How can we correct the $$n$$th-degree Taylor polynomial to a graph at $$a$$ so that it also coincides with the graph at some $$b \neq a$$? (We'll then see what needs to happen for the needed correction to vanish $$\forall b \neq a$$.) For this correction, we'll introduce some constant $$M$$, which we'll add on to the end of our Taylor polynomial in some way. Where $$P^*$$ is the corrected Taylor polynomial, this $$M$$ will need to be such that $$P^*(b) = f(b)$$ while still maintaining that $$P^*(a) = f(a), \left.\frac{dP^*}{dx}\right\rvert_a = \left.\frac{df}{dx}\right\rvert_a, ..., \left.\frac{d^nP^*}{dx^n}\right\rvert_a = \left.\frac{d^nf}{dx^n}\right\rvert_a$$. This means that simply defining, e.g.,

$$P^* \colon x \longmapsto \sum_{k = 1}^n \frac{1}{k!} \left.\frac{d^kf}{dx^k}\right\rvert_{a} (x - a)^k + f(a) + M \; \forall x \in \mathbb{R}$$

isn't enough: We need to engineer a correction term such that it doesn't interfere with the key properties of the Taylor polynomial at $$a$$. So here's what we'll do: Define

$$P^* \colon x \longmapsto \sum_{k = 1}^n \frac{1}{k!} \left.\frac{d^kf}{dx^k}\right\rvert_{a} (x - a)^k + f(a) + M(x - a)^{n + 1} \; \forall x \in \mathbb{R}.$$

This way, by [Sum Rule](/differential-calculus#theorem-sum-rule) and [Power Rule](/differential-calculus#theorem-power-rule), the first through $$n$$th derivatives of $$P^*(x)$$ with respect to $$x$$ remain unchanged when $$x = a$$ since the correction term's first through $$n$$th derivatives are zero when $$x = a$$.

Having reached a satisfactory definition for $$P^*$$, we now turn our attention to the difference between $$f$$ and $$P^*$$,

$$D \coloneqq f - P^*.$$

Notice that by the definition of $$M$$, we have $$D(a) = 0 = D(b)$$. We should probably also have that $$f(x)$$ is $$n$$ times differentiable with respect to $$x$$ $$\forall x \in [a,b]$$ as it would probably be difficult to use an $$n$$ times differentiable function to approximate a portion of a function that is not $$n$$ times differentiable. $$D(x)$$ is then also $$n$$ times differentiable with respect to $$x$$ $$\forall x \in [a,b]$$, and so we must have

$$\left.\frac{dD}{dx}\right\rvert_{\gamma_1} = 0 \; \exists \gamma_1 \in (a,b)$$

by [Rolle's Theorem](/differential-calculus#rolles-theorem). But then we have that 

$$\left.\frac{dD}{dx}\right\rvert_a = 0 = \left.\frac{dD}{dx}\right\rvert_{\gamma_1}$$

with $$D$$ differentiable on $$[a,\gamma_1]$$, so we can apply [Rolle's Theorem](/differential-calculus#rolles-theorem) again, yielding

$$\left.\frac{d^2D}{dx^2}\right\rvert_{\gamma_2} = 0 \; \exists \gamma_2 \in (a,\gamma_1),$$

but then we can do the same thing again, and so on until reaching

$$\left.\frac{d^nD}{dx^n}\right\rvert_{\gamma_n} = 0 \; \exists \gamma_n \in (a,\gamma_{n-1}),$$

and if we finally assume $$f$$ to be differentiable one more time (which we should if we're planning on letting $$n \longrightarrow \infty$$), we arrive at 

$$\left.\frac{d^{n+1}D}{dx^{n+1}}\right\rvert_\gamma = \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma - M \cdot (n+1)! = 0 \implies M = \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma \cdot \frac{1}{(n+1)!} \; \exists \gamma \in (a,\gamma_n) \subset (a,b)$$

by [Sum Rule](/differential-calculus#theorem-sum-rule) and [Power Rule](/differential-calculus#theorem-power-rule). So, as long as

$$\lim_{n \to \infty} \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma \cdot \frac{(x - a)^{n+1}}{(n+1)!} = 0 \; \forall x \in [a,b], \gamma \in (a,x),$$

we'll be guaranteed to have a perfect approximation of $$f$$ on $$[a,b]$$. (This result about the correction term, by the way, is called Taylor's theorem.)

## Taylor's Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ be $$n + 1$$ times differentiable at $$x$$ $$\forall x \in [a,b]$$ $$\exists a,b \in \mathbb{R}, n \in \mathbb{Z} > 0$$. Let $$P$$ be the degree $$n$$ Taylor polynomial to $$f$$ at $$a$$. Then

$$\exists \gamma \in (a,b) \text{ or } (b,a) \mid f(b) = P(b) + \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma \cdot \frac{(b-a)^{n+1}}{(n+1)!}.$$

**Proof.** Let $$M$$ be the constant such that 

$$P(b) + M(b-a)^{n+1} = f(b).$$

Let 

$$D(x) = f(x) - P(x) - M(x-a)^{n+1}.$$

$$D(x)$$ is $$n+1$$ times differentiable at $$x$$ $$\forall x \in [a,b]$$.

$$D(b) = D(a) = \left.\frac{dD}{dx}\right\rvert_a = \left.\frac{d^2D}{dx^2}\right\rvert_a = \cdots = \left.\frac{d^nD}{dx^n}\right\rvert_a = 0.$$

Therefore, after applying [Differentiable Implies Continuous](/differential-calculus#theorem-differentiable-implies-continuous), by [Rolle's Theorem](/differential-calculus#rolles-theorem), 

$$\exists \gamma_1 \in (a,b) \mid \left.\frac{dD}{dx}\right\rvert_{\gamma_1} = 0 \implies \exists \gamma_2 \in (a,\gamma_1) \subset (a,b) \mid \left.\frac{d^2D}{dx^2}\right\rvert_{\gamma_2} = 0 \implies \cdots \implies \exists \gamma_n \in (a,b) \mid \left.\frac{d^nD}{dx^n}\right\rvert_{\gamma_n} = 0 \implies \exists \gamma \in (a,b) \mid \left.\frac{d^{n+1}D}{dx^{n+1}}\right\rvert_\gamma = \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma - M \cdot (n+1)! = 0 \implies M = \left.\frac{d^{n+1}f}{dx^{n+1}}\right\rvert_\gamma \cdot \frac{1}{(n+1)!}. \text{ } \Box$$

---

Okay, so what should we try making a Taylor series for first? it's going to have to be something interesting (here, that means not a polynomial) that we know for sure we can infinitely differentiate.... How about $$e^x$$? That's clearly infinitely differentiable with respect to $$x$$ $$\forall x \in \mathbb{R}$$. Let's see if its correction term goes to zero:

$$\lim_{n \to \infty} \left.\frac{d^{n+1}(e^x)}{dx^{n+1}}\right\rvert_\gamma \cdot \frac{(x - a)^{n+1}}{(n+1)!} = e^\gamma \lim_{n \to \infty} \frac{(x - a)^{n+1}}{(n+1)!} = 0 \; \forall \gamma, x, a \in \mathbb{R}$$

indeed since eventually $$(n+1)!$$ will start growing more rapidly than $$(x - a)^{n+1}$$ regardless of what $$x - a$$ is. Therefore we're guaranteed that the Taylor series for $$e^x$$ works everywhere, so we might as well center it at $$0$$:

$$1 + \sum_{k = 1}^{\infty} \frac{x^k}{k!} = e^x \; \forall x \in \mathbb{R}.$$

This also means we can arrive at an exact value for $$e$$ by letting $$x = 1$$:

$$e = 1 + \sum_{k = 1}^{\infty} \frac{1}{k!} \approx 2.718281828459045.$$

And that's pretty much it for differential calculus! (Though you should really [buy the DLC](/topic/trigonometry).) As a trophy symbolic of our crowning achievement in this endeavor, I'll leave you with [this Desmos graph](https://www.desmos.com/calculator/eblplrkvdb) where you can watch our Taylor series converge to $$e^x$$ as $$n$$ grows.
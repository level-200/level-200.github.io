---
title: Trigonometry*
permalink: /trigonometry
nav_order: 5
---

# Trigonometry

Let's start off with a very simple question. What's an angle? We all have a loose idea of what an angle is—Given two lines that intersect at a point, the angle between them is the amount of pivoting about that point that one line would have to do to line up with the other—But if you showed me a particular angle, how would I be able to verify if that were, say, $$48$$ degrees or not? Sure, we could arbitrarily define it by making up a protractor, but then basing all other protractors on that one would be rather cumbersome. We'd like to be able to simply inspect the angle and tell. 

The most trivial case to define an angle for would be the case where there is no angle—The two lines overlap perfectly. We can define that straight away as an angle of $$0$$. After that, as one line (the *terminal side*) departs from the other (the *initial side*), it gets more tricky, but we know that eventually the terminal side will come back to where it started, having gone in a circle, and that the further around the circle it has gone, the bigger the angle will be (and we expect this relationship to be linear). And that's the key to properly defining the angle formed by the terminal and initial sides: The *arc length* (i.e., distance along the edge of the circle) between them. The only trick after that is to realize that the radius of the circle shouldn't matter as far as the angle is concerned, and so we need to normalize: Define

$$\text{Angle} \propto \frac{\text{Arc length}}{\text{Radius}}$$

(since $$\text{Arc length} \coloneqq \text{Portion of circumference} \propto \text{Radius}$$), with the constant of proportionality just coming down to a choice of units. This suggests that the most "natural" unit of angle is not, in fact, degrees, but is actually *radians*, the unit for which the constant of proportionality is $$1$$.

## Definition: Radians

For any given angle, where $$s$$ is the arc length of the portion of a circle of constant radius $$r$$ that may be inscribed between the angle's initial and terminal sides, the measure of that angle in radians is defined as

$$\frac{s}{r}.$$

---

We'll adopt these as our standard unit of angle from now on. This means a full circle will be $$2\pi \text { rad}$$, a half circle will be $$\pi \text { rad}$$, a right angle will be $$\frac{\pi}{2} \text { rad}$$, etc.

Now, what if I wanted to define a function that measures the height of a given angle? With some further specification, it seems like it should be possible; as I change an angle around (picture, e.g., the minute hand of a clock as it goes in a circle over the course of an hour), there's only one possible amount its terminal end can "stick up" at any instant. However, we will need to have a standard choice of where the initial end is, which direction the terminal end is going, and how long the terminal end is before we can expect to find a single possible height for a given angle. These are pretty arbitrary, but the convention is, respectively: Sticking out directly to the right, counter-clockwise, and $$1$$. This means the tip of the terminal end traces out a *unit circle*, a circle of radius $$1$$. We call the function that returns the height of the angle (the angle being in radians) given these conditions $$\sin$$ (*sine*).

Note that it's pretty easy to go from these particular conditions to others: To start at a different spot, just add the appropriate offset to the argument of $$\sin$$; to go the other way, just negate the argument; and to have a radius of $$r$$ rather than one, just use $$r \cdot \sin$$ instead (if you, e.g., double a line segment's length, it will stick up by twice as much). So, we're not losing much generality here.

This means $$\sin \theta$$ is well-defined $$\forall \theta \in \mathbb{R}$$; it's obviously well-defined for $$\theta \geq 0$$, and $$\theta \leq 0$$ just means we went clockwise rather than counter-clockwise. So its domain is $$\mathbb{R}$$, and its range is pretty easy to see, too: As we go around the circle (as $$\theta$$ increases from $$0$$ to $$2\pi$$), we go from flat ($$\sin 0 = 0$$) to sticking all the way up ($$\sin \frac{\pi}{2} = 1$$) to flat again ($$\sin \pi = 0$$) to sticking all the way down ($$\sin \frac{3\pi}{2} = -1$$) to flat again ($$\sin 2\pi = 0$$), so $$\sin$$'s range is $$[-1, 1]$$.

For $$\theta \in (0, \frac{\pi}{2})$$, there's another way of thinking of $$\sin$$ as well: We can picture a right triangle with $$\theta$$ as one of its angles, and $$\sin \theta$$ is the ratio of the lengths of the side opposite $$\theta$$ and the hypotenuse:

$$\sin \theta = \frac{\text{Height}}{\text{Terminal side length}} = \frac{\text{Opposite}}{\text{Hypotenuse}}.$$

We can also define a function $$\cos$$ (*cosine*) that returns how much an angle sticks out to the right under the same conditions and see that $$\cos$$ has the same domain and range as $$\sin$$ and that for $$\theta \in (0, \frac{\pi}{2})$$, in that same triangle context,

$$\cos \theta = \frac{\text{"Jut-out"}}{\text{Terminal side length}} = \frac{\text{Adjacent}}{\text{Hypotenuse}}.$$

There are also some other, less prominent individuals in the family of *trigonometric ratios*.

## Definition: Tangent

$$\tan \coloneqq \frac{\sin}{\cos}.$$

---

(Note that $$\tan$$ measures the slope of the terminal end.)

## Definition: Secant

$$\sec \coloneqq \frac{1}{\cos}.$$

## Definition: Cosecant

$$\csc \coloneqq \frac{1}{\sin}.$$

## Definition: Cotangent

$$\cot \coloneqq \frac{\cos}{\sin}.$$

---

(Notice that $$\cot = \frac{1}{\tan}$$ almost everywhere, but $$\cot$$ and $$\frac{1}{\tan}$$ differ in where they are undefined.)

You'll notice, however, that we haven't actually given a definition for $$\sin$$ and $$\cos$$ yet. That's because we don't really have one. We have some inspiration for one, but nothing formal yet. Let's see if we can fix that.

We happen to have developed a tool that, if we're lucky, will tell us exactly what $$\sin \theta$$ and $$\cos \theta$$ are $$\forall \theta \in \mathbb{R}$$ (by way of a Taylor series): Taylor's theorem. However, there is a prerequisite here: Smoothness. Are $$\sin$$ and $$\cos$$ differentiable even once?

Well, if we center our unit circle at $$(0,0)$$ in the $$\mathbb{R}^2$$ plane, then $$(\cos \theta, \sin \theta)$$ is our position vector, and $$\frac{d}{d\theta} (\cos \theta, \sin \theta)$$ is a velocity vector. But that, if it exists, will be tangent to the circle's edge, which definitely ought to admit a tangent vector; it's locally linear. So, we can pretty confidently guess that $$\sin \theta$$ and $$\cos \theta$$ are differentiable with respect to $$\theta$$ $$\forall \theta \in \mathbb{R}$$. Okay, cool. But what are their derivatives?

Well, since this is a circle, our velocity vector should just be proportional to a ninety-degree counter-clockwise rotation of our position vector (position and velocity must be perpendicular as otherwise radius would not be constant, and we're going counter-clockwise by definition). So,

$$\frac{d}{d\theta} (\cos \theta, \sin \theta) = k(-\sin \theta, \cos \theta) \; \exists k \in \mathbb{R} > 0 \; \forall \theta \in \mathbb{R}.$$

Now, because we're using radians and because this is a circle of unit radius, we know that $$\theta$$ will just be how far along the circle's edge we've travelled. So, our position will be changing at a rate of one unit per radian, and thus our velocity will have a magnitude of $$1$$. This means $$k = 1$$: Our radius is $$1$$, so the magnitude of our position is $$1$$, and the magnitude of our velocity will be $$k$$ times the magnitude of our position. Therefore

$$\frac{d}{d\theta} (\cos \theta, \sin \theta) = (-\sin \theta, \cos \theta) \Longrightarrow \frac{d(\sin \theta)}{d\theta} = \cos \theta, \frac{d(\cos \theta)}{d\theta} = -\sin \theta \; \forall \theta \in \mathbb{R}.$$

So $$\sin$$ and $$\cos$$ are both smooth everywhere in $$\mathbb{R}$$ since both are differentiable everywhere in $$\mathbb{R}$$ and each's derivative is plus or minus the other, which is, of course, itself differentiable. Thus, we can apply Taylor's theorem: $$\forall b, a \in \mathbb{R} \mid b \neq a, n \in \mathbb{Z} > 0 \; \exists \gamma \in (a,b) \text{ or } (b,a) \mid$$

$$\sin b = \sum_{k = 1}^n \left.\frac{d^k(\sin \theta)}{d\theta^k}\right\rvert_a \cdot \frac{(b - a)^k}{k!} + \sin a + \left.\frac{d^{n+1}(\sin \theta)}{d\theta^{n+1}}\right\rvert_\gamma \cdot \frac{(b - a)^{n + 1}}{(n+1)!},$$

$$\cos b = \sum_{k = 1}^n \left.\frac{d^k(\cos \theta)}{d\theta^k}\right\rvert_a \cdot \frac{(b - a)^k}{k!} + \cos a + \left.\frac{d^{n+1}(\cos \theta)}{d\theta^{n+1}}\right\rvert_\gamma \cdot \frac{(b - a)^{n + 1}}{(n+1)!},$$

and since

$$\lim_{n \to \infty} \left.\frac{d^{n+1}(\sin \theta)}{d\theta^{n+1}}\right\rvert_\gamma \cdot \frac{(b - a)^{n + 1}}{(n+1)!} = \lim_{n \to \infty} \left.\frac{d^{n+1}(\cos \theta)}{d\theta^{n+1}}\right\rvert_\gamma \cdot \frac{(b - a)^{n + 1}}{(n+1)!} = 0 \; \forall a, b, \gamma \in \mathbb{R}$$

(neither $$\frac{d^{n+1}(\sin \theta)}{d\theta^{n+1}}$$ nor $$\frac{d^{n+1}(\cos \theta)}{d\theta^{n+1}}$$ can ever be outside of $$[-1,1]$$, and $$\frac{(b - a)^{n + 1}}{(n+1)!}$$ shrinks to zero as $$n \longrightarrow \infty$$ since the factorial in the denominator eventually outpaces the exponential in the numerator), we have that (letting $$b = x$$ and $$a = 0$$)

$$\sin x = \sum_{k = 1}^\infty \left.\frac{d^k(\sin \theta)}{d\theta^k}\right\rvert_0 \cdot \frac{x^k}{k!} + \sin 0 = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots,$$

$$\cos x = \sum_{k = 1}^\infty \left.\frac{d^k(\cos \theta)}{d\theta^k}\right\rvert_0 \cdot \frac{x^k}{k!} + \cos 0 = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots$$

$$\forall x \in \mathbb{R}$$ since $$\sin 0 = 0$$ and $$\cos 0 = 1$$.

## Definition: Sine

$$\sin \coloneqq x \longmapsto x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots \; \forall x \in \mathbb{R}.$$

## Definition: Cosine

$$\cos \coloneqq x \longmapsto 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots \; \forall x \in \mathbb{R}.$$

---

Now we need to check that $$\sin$$ and $$\cos$$ work like we expect them to.

These first two results are needed just to make sure they work at all:

## Theorem: Sine Converges

$$\sin x$$ is well-defined $$\forall x \in \mathbb{R}$$.

**Proof.** Let $$x \geq 0$$. By [Definition: Sine](/trigonometry#definition-sine),

$$\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots \leq x + \frac{x^3}{3!} + \frac{x^5}{5!} + \frac{x^7}{7!} + \frac{x^9}{9!} + \cdots < 1 + \sum_{k = 1}^{\infty} \frac{x^k}{k!}.$$

But using [Taylor's Theorem](/differential-calculus#taylors-theorem), it may be shown that

$$e^x = 1 + \sum_{k = 1}^{\infty} \frac{x^k}{k!} \; \forall x \in \mathbb{R}$$

(see the end of [Differential Calculus](/differential-calculus)).

$$e^x$$ is well-defined. Therefore $$\sin x$$ must converge to a finite value $$\forall x \geq 0$$.

$$\sin(-x) = -\sin x \; \forall x \geq 0.$$

Thus, $$\sin x$$ is well-defined $$\forall x \in \mathbb{R}$$. $$\Box$$

## Theorem: Cosine Converges

$$\cos x$$ is well-defined $$\forall x \in \mathbb{R}$$.

**Proof.** It follows from [Definition: Cosine](/trigonometry#definition-cosine) that

$$\cos(-x) = \cos x \; \forall x \geq 0.$$

Thus, it suffices to prove the result for $$x \geq 0$$. Now, $$\forall x \geq 0$$, by [Definition: Cosine](/trigonometry#definition-cosine),

$$\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots \leq 1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \frac{x^6}{6!} + \frac{x^8}{8!} + \cdots \leq 1 + \sum_{k = 1}^{\infty} \frac{x^k}{k!}.$$

But using [Taylor's Theorem](/differential-calculus#taylors-theorem), it may be shown that

$$e^x = 1 + \sum_{k = 1}^{\infty} \frac{x^k}{k!} \; \forall x \in \mathbb{R}$$

(see the end of [Differential Calculus](/differential-calculus)).

$$e^x$$ is well-defined. Therefore $$\cos x$$ must converge to a finite value. $$\Box$$

---

And then these next two are shoo-ins:

## Theorem: Derivative of Sine

$$\forall x \in \mathbb{R}$$,

$$\frac{d(\sin x)}{dx} = \cos x.$$

**Proof.** By [Sum Rule](/differential-calculus#theorem-sum-rule), [Constant Factor Rule](/differential-calculus#theorem-constant-factor-rule), [Power Rule](/differential-calculus#theorem-power-rule), [Derivative With Respect to Self](/differential-calculus#theorem-derivative-with-respect-to-self), [Definition: Sine](/trigonometry#definition-sine), and [Definition: Cosine](/trigonometry#definition-cosine),

$$\frac{d(\sin x)}{dx} = 1 - 3\frac{x^2}{3!} + 5\frac{x^4}{5!} - 7\frac{x^6}{7!} + 9\frac{x^8}{9!} - \cdots = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots = \cos x$$

$$\forall x \in \mathbb{R}$$. $$\Box$$

## Theorem: Derivative of Cosine

$$\forall x \in \mathbb{R}$$,

$$\frac{d(\cos x)}{dx} = -\sin x.$$

**Proof.** By [Sum Rule](/differential-calculus#theorem-sum-rule), [Constant Factor Rule](/differential-calculus#theorem-constant-factor-rule), [Power Rule](/differential-calculus#theorem-power-rule), [Constant Rule](/differential-calculus#theorem-constant-rule), [Definition: Cosine](/trigonometry#definition-cosine), and [Definition: Sine](/trigonometry#definition-sine),

$$\frac{d(\cos x)}{dx} = 0 - 2\frac{x}{2!} + 4\frac{x^3}{4!} - 6\frac{x^5}{6!} + 8\frac{x^7}{8!} - 10\frac{x^9}{10!} + \cdots = -(x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots) = -\sin x$$

$$\forall x \in \mathbb{R}$$. $$\Box$$

---

But now we ought to pause and ask ourselves how much we need to prove here. All we really want to show is that $$(\cos \theta, \sin \theta)$$ is that point on that unit circle we described earlier, right? We already have, from the four results above, that the point exists and $$\frac{d}{d\theta} (\cos \theta, \sin \theta)$$ is just $$(\cos \theta, \sin \theta)$$ rotated $$90 \text{ deg}$$ (err, I mean $$\frac{\pi}{2} \text{ rad}$$) counterclockwise. So, that's already enough to know that we're going in a circle; velocity is perpendicular to position. It's also trivial to show that $$(\cos 0, \sin 0) = (1, 0)$$, so we're starting in the right place and have the right radius. So as long our speed is right, we're good to go. But our speed is identically equal in magnitude to our radius, which is $$1$$! So we're good. $$\sin$$ and $$\cos$$ are everything we wanted them to be.

If you want something more rigorous than "radius starts at $$1$$ and velocity is perpendicular to position, so radius must stay at $$1$$," though, (and you probably should), here you go. One piece of notation is prerequisite.

## Notation: Exponentiated Trigonometric Ratios

$$\forall x, n \in \mathbb{R}$$,

$$(\sin x)^n \coloneqq \sin^n x,$$

$$(\cos x)^n \coloneqq \cos^n x,$$

and similarly for other trigonometric ratios.

## Theorem: Pythagorean Trigonometric Identity

$$\cos^2 x + \sin^2 x = 1 \; \forall x \in \mathbb{R}.$$

**Proof.** By [Sum Rule](/differential-calculus#theorem-sum-rule), [Power Rule](/differential-calculus#theorem-power-rule), [Chain Rule](/differential-calculus#theorem-chain-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), and [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine),

$$\frac{d}{dx}(\cos^2 x + \sin^2 x) = 2 \cos x (- \sin x) + 2 \sin x \cos x = 0 \; \forall x \in \mathbb{R}.$$

Therefore $$\cos^2 0 + \sin^2 0 = \cos^2 x + \sin^2 x$$ $$\forall x \in \mathbb{R}$$ by [Taylor's Theorem](/differential-calculus#taylors-theorem) and [Constant Rule](/differential-calculus#theorem-constant-rule).

$$\cos^2 0 + \sin^2 0 = 1^2 + 0^2 = 1$$

by [Definition: Cosine](/trigonometry#definition-cosine) and [Definition: Sine](/trigonometry#definition-sine). $$\Box$$

---

So $$\sin$$ and $$\cos$$ are exactly what we wanted! Have [this Desmos graph](https://www.desmos.com/calculator/ncfitc7kha) as a prize and a demonstration of our work thus far.

There is something else to address, though. You may have noticed, and it was hinted at in the proofs that $$\sin$$ and $$\cos$$ are well-defined, that the definitions of $$\sin x$$ and $$\cos x$$ look rather similar to the Taylor series for $$e^x$$. In fact, if it weren't for those pesky negative signs, we'd have $$\sin x + \cos x = e^x$$. I wonder if we could modify the exponent $$e$$ is being raised to so as to end up with negative signs where we need them to be. But wait, because the definition of $$\cos$$ only involves even powers, we'd somehow need the modified exponent to potentially give a negative number when raised to an even power, and that's not something any real number can do. But who said anything about being restrained to real numbers? Check it out:

$$e^{ix} = 1 + ix + \frac{(ix)^2}{2!} + \frac{(ix)^3}{3!} + \frac{(ix)^4}{4!} + \frac{(ix)^5}{5!} + \frac{(ix)^6}{6!} + \frac{(ix)^7}{7!} + \frac{(ix)^8}{8!} + \frac{(ix)^9}{9!} + \cdots = 1 + ix - \frac{x^2}{2!} - i\frac{x^3}{3!} + \frac{x^4}{4!} + i\frac{x^5}{5!} - \frac{x^6}{6!} - i\frac{x^7}{7!} + \frac{x^8}{8!} + i\frac{x^9}{9!} - \cdots = (1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots) + i(x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots) = \cos x + i\sin x \; \forall x \in \mathbb{R},$$

where, of course, $$i$$ is our good friend the imaginary unit, a constant with the property

$$i^2 = -1.$$

This allows for an interesting visualization of complex numbers; if, on a standard two-dimensional plane, we graph the imaginary part of a complex number on the vertical axis and the real part on the horizontal axis (forming the *complex plane*), then for fixed $$r \geq 0$$,

$$\{re^{i\theta} \mid \theta \in \mathbb{R}\}$$

forms a circle of radius $$r$$, and so, e.g.,

$$e^{i\frac{\pi}{2}} = i,$$

and, of course, the famous

$$e^{i\pi} = -1$$

or

$$e^{i\pi} + 1 = 0,$$

which is pretty cool—It relates five of the most important constants in math (and does so using some of the most important concepts in math, too—Infinity, limits, circles, etc.). This is perhaps the biggest reason why [Euler](https://en.wikipedia.org/wiki/Leonhard_Euler) was goated: He was the first to notice this.

By the way, you may be scratching your head, and rightfully so, at the notion of raising a number to an imaginary exponent. That's an idea that's multiple degrees removed from the more down-to-earth concept of repeated multiplication. So, at this level of abstraction, we tend to use the *exponential* function instead, defined as follows, as a way of generalizing the notion of exponentiating $$e$$.

## Definition: Exponential

$$\exp \coloneqq z \longmapsto 1 + \sum_{k = 1}^{\infty} \frac{z^k}{k!} \; \forall z \in \mathbb{C}.$$

---

Anyway, our discovery is named in honor of Euler.

## Theorem: Euler's Formula

$$\exp(ix) = \cos x + i\sin x \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Exponential](/trigonometry#definition-exponential), [Definition: Cosine](/trigonometry#definition-cosine), and [Definition: Sine](/trigonometry#definition-sine), 

$$\exp(ix) = 1 + ix + \frac{(ix)^2}{2!} + \frac{(ix)^3}{3!} + \frac{(ix)^4}{4!} + \frac{(ix)^5}{5!} + \frac{(ix)^6}{6!} + \frac{(ix)^7}{7!} + \frac{(ix)^8}{8!} + \frac{(ix)^9}{9!} + \cdots = 1 + ix - \frac{x^2}{2!} - i\frac{x^3}{3!} + \frac{x^4}{4!} + i\frac{x^5}{5!} - \frac{x^6}{6!} - i\frac{x^7}{7!} + \frac{x^8}{8!} + i\frac{x^9}{9!} - \cdots = (1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \frac{x^8}{8!} - \cdots) + i(x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \cdots) = \cos x + i\sin x \; \forall x \in \mathbb{R}. \text{ } \Box$$

---

Now we turn our attention to deriving some *trigonometric identities*. There's a whole family of these; we'll just prove most of the results on $$\sin$$ and $$\cos$$ here. However, you should know that analogous identities can be derived from these for $$\tan$$, $$\sec$$, $$\csc$$, and $$\cot$$ just by using each's definition in terms of $$\sin$$ and $$\cos$$ together with the corresponding identities for $$\sin$$ and $$\cos$$.

This first result might seem a little random. We can provide a justification for why we might expect it to be true using [something like this](https://en.wikipedia.org/wiki/Proofs_of_trigonometric_identities#Angle_sum_identities). However, be sure not to confuse this reasoning with a proper proof as it only covers $$a, b > 0, a + b < \frac{\pi}{2}$$ and strictly speaking, we don't have a justification for much of the geometric reasoning used.

## Theorem: Sine and Cosine of Sum

$$\forall a, b \in \mathbb{R}$$,

$$\sin(a + b) = \sin a \cos b + \sin b \cos a,$$

$$\cos(a + b) = \cos a \cos b - \sin a \sin b.$$

**Proof.** Fixing $$b$$, let

$$f(a) = \sin(a + b) - \sin a \cos b - \sin b \cos a,$$

$$g(a) = \cos(a + b) - \cos a \cos b + \sin a \sin b.$$

By [Sum Rule](/differential-calculus#theorem-sum-rule), [Chain Rule](/differential-calculus#theorem-chain-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine), [Constant Rule](/differential-calculus#theorem-constant-rule), [Derivative With Respect to Self](/differential-calculus#theorem-derivative-with-respect-to-self), and [Product Rule](/differential-calculus#theorem-product-rule),

$$\frac{df}{da} = \cos(a + b) - \cos a \cos b + \sin a \sin b = g(a),$$

$$\frac{dg}{da} = -\sin(a + b) + \sin a \cos b + \cos a \sin b = -f(a),$$

so by [Power Rule](/differential-calculus#theorem-power-rule),

$$\frac{d}{da}((f(a))^2 + (g(a))^2) = 2f(a)\frac{df}{da} + 2g(a)\frac{dg}{da} = 2f(a)g(a) + 2g(a)(-f(a)) = 0.$$

Thus, by [Taylor's Theorem](/differential-calculus#taylors-theorem), [Definition: Sine](/trigonometry#definition-sine), and [Definition: Cosine](/trigonometry#definition-cosine),

$$(f(a))^2 + (g(a))^2 = (f(0))^2 + (g(0))^2 = (\sin(b) - 0 \cdot \cos b - \sin b \cdot 1)^2 + (\cos(b) - 1 \cdot \cos b + 0 \cdot \sin b)^2 = 0.$$

But

$$(f(a))^2, (g(a))^2 \geq 0.$$

Therefore

$$(f(a))^2 = 0 = (g(a))^2 \Longrightarrow f(a) = 0 = g(a).$$

$$f(a) = \sin(a + b) - \sin a \cos b - \sin b \cos a = 0 \Longrightarrow \sin(a + b) = \sin a \cos b + \sin b \cos a,$$

$$g(a) = \cos(a + b) - \cos a \cos b + \sin a \sin b = 0 \Longrightarrow \cos(a + b) = \cos a \cos b - \sin a \sin b. \text{ } \Box$$

---

Notice that this result can be used to derive identities for $$\sin(a - b), \cos (a - b)$$ just by swapping $$b$$ for $$-b$$ and using $$\cos(-x) = \cos x, \sin(-x) = -\sin x$$.

## Theorem: Double Angle Identities

$$\forall \theta \in \mathbb{R}$$,

$$\sin(2\theta) = 2\sin \theta \cos \theta,$$

$$\cos(2\theta) = \cos^2 \theta - \sin^2 \theta = 1 - 2\sin^2 \theta = 2\cos^2 \theta - 1.$$

**Proof.** By [Sine and Cosine of Sum](/trigonometry#theorem-sine-and-cosine-of-sum),

$$\sin(2\theta) = \sin(\theta + \theta) = \sin \theta \cos \theta + \sin \theta \cos \theta = 2\sin \theta \cos \theta,$$

$$\cos(2\theta) = \cos(\theta + \theta) = \cos \theta \cos \theta - \sin \theta \sin \theta = \cos^2 \theta - \sin^2 \theta = 1 - 2\sin^2 \theta = 2\cos^2 \theta - 1$$

by [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity). $$\Box$$

## Theorem: Half Angle Identities

$$\forall \theta \in \mathbb{R}$$,

$$\sin \left(\frac{\theta}{2} \right) = \pm \sqrt{\frac{1 - \cos \theta}{2}},$$

$$\cos \left(\frac{\theta}{2} \right) = \pm \sqrt{\frac{1 + \cos \theta}{2}}.$$

**Proof.** By [Double Angle Identities](/trigonometry#theorem-double-angle-identities),

$$\cos(2\theta) = 1 - 2\sin^2 \theta \Longrightarrow \cos(\theta) = 1 - 2\sin^2 \left(\frac{\theta}{2} \right) \Longrightarrow \frac{1 - \cos \theta}{2} = \sin^2 \left(\frac{\theta}{2} \right) \Longrightarrow \sin \left(\frac{\theta}{2} \right) = \pm \sqrt{\frac{1 - \cos \theta}{2}},$$

$$\cos(2\theta) = 2\cos^2(\theta) - 1 \Longrightarrow \cos \theta = 2\cos^2 \left (\frac{\theta}{2} \right) - 1 \Longrightarrow \frac{1 + \cos \theta}{2} = \cos^2 \left(\frac{\theta}{2} \right) \Longrightarrow \cos \left(\frac{\theta}{2} \right) = \pm \sqrt{\frac{1 + \cos \theta}{2}}. \text{ } \Box$$

## Theorem: Trigonometric Power Reduction Identities

$$\forall \theta \in \mathbb{R}$$,

$$\sin^2 \theta = \frac{1 - \cos(2\theta)}{2},$$

$$\cos^2 \theta = \frac{1 + \cos(2\theta)}{2}.$$

**Proof.** By [Double Angle Identities](/trigonometry#theorem-double-angle-identities),

$$\cos(2\theta) = 1 - 2\sin^2 \theta \Longrightarrow \sin^2 \theta = \frac{1 - \cos(2\theta)}{2},$$

$$\cos(2\theta) = 2\cos^2(\theta) - 1 \Longrightarrow \cos^2 \theta = \frac{1 + \cos(2\theta)}{2}. \text{ } \Box$$

---

One more thing we can define is functions that return an angle given the value of a certain trigonometric ratio for that angle. That is, *inverse trigonometric functions*. However, none of our trigonometric functions are injective everywhere; every $$2\pi \text{ rad}$$, you end up back in the same spot on the unit circle. This means if we want to define these inverses, we need to restrict ourselves to a certain set of angles where invertibility holds. $$[-\frac{\pi}{2}, \frac{\pi}{2}]$$, for example, is the biggest region we can manage to have $$\sin$$ be invertible; going from $$-\frac{\pi}{2} \text{ rad}$$ to $$\frac{\pi}{2} \text{ rad}$$ goes from sticking straight down to sticking straight up, and any further past either boundary means repeating a height value. We'll cover how we do this for each function one by one. (We'll also need to find the set of values the function covers on that interval—The domain of its inverse—But that's not as tricky.)

One other thing to note is that we ought to avoid the standard notation for inverse functions here; $$\sin^{-1}$$, e.g., is already defined to be $$\sin$$ raised to the power of $$-1$$. Instead, we denote inverse trigonometric functions with the prefix $$\text{arc}$$.

## Definition: Arcsine

$$\arcsin \coloneqq x \longmapsto \theta \mid x = \sin \theta, \theta \in \left[-\frac{\pi}{2}, \frac{\pi}{2} \right] \; \forall x \in [-1, 1].$$

---

Finding where $$\cos$$ is invertible is a similar deal as with $$\sin$$: On $$[0, \pi]$$, we go from sticking out straight to the right to sticking out straight to the left, and any farther either way means repeating a "jut-out" value. 

## Definition: Arccosine

$$\arccos \coloneqq x \longmapsto \theta \mid x = \cos \theta, \theta \in [0, \pi] \; \forall x \in [-1, 1].$$

---

As for $$\tan$$, recall that $$\tan \theta$$ measures the slope of the angle $$\theta$$, and also notice $$\tan \left(-\frac{\pi}{2} \right)$$ and $$\tan \left(\frac{\pi}{2} \right)$$ are undefined. This means $$(-\frac{\pi}{2}, \frac{\pi}{2})$$ is the best we can do: On that interval, we rotate from a very steep downward slope to a very steep upward slope; any greater than $$\frac{\pi}{2} \text{ rad}$$ or less than $$-\frac{\pi}{2} \text{ rad}$$ and we repeat a slope value.

## Definition: Arctangent

$$\arctan \coloneqq x \longmapsto \theta \mid x = \tan \theta, \theta \in \left(-\frac{\pi}{2}, \frac{\pi}{2} \right) \; \forall x \in \mathbb{R}.$$

---

The reciprocals of $$\sin$$ and $$\cos$$ are then invertible on the same sets of angles; $$\frac{1}{x}$$ is only repeated if $$x$$ is.

## Definition: Arccosecant

$$\operatorname{arccsc} \coloneqq x \longmapsto \theta \mid x = \csc \theta, \theta \in \left[-\frac{\pi}{2},0 \right) \cup \left(0, \frac{\pi}{2} \right] \; \forall x \in (-\infty, -1] \cup [1, \infty).$$

## Definition: Arcsecant

$$\operatorname{arcsec} \coloneqq x \longmapsto \theta \mid x = \sec \theta, \theta \in \left[0, \frac{\pi}{2} \right) \cup \left(\frac{\pi}{2}, \pi \right] \; \forall x \in (-\infty, -1] \cup [1, \infty).$$

---

We do $$\operatorname{arccot}$$ a little differently, though, because $$\cot$$ is not quite the reciprocal of $$\tan$$. Because it's $$\frac{\cos}{\sin}$$, it basically measures "flatness," the opposite of slope. So, a flat line has infinite (undefined) flatness, and as we increase from $$0 \text{ rad}$$, we get less and less flat until hitting $$0$$ flatness at $$\frac{\pi}{2} \text{ rad}$$ (sticking straight up), then we have more and more negative flatness (flatness with the opposite orientation) until we hit infinite (undefined) negative flatness again at $$\pi \text{ rad}$$. So, while we could just define $$\operatorname{arccot} \in \left[-\frac{\pi}{2}, 0 \right) \cup \left(0, \frac{\pi}{2} \right]$$ to be consistent with $$\arctan$$ (notwithstanding the inclusion of the boundary and the exclusion of $$0$$ due to $$\tan$$ and $$\cot$$ not being undefined in the same places), it's a bit cleaner (and indicative that $$\cot$$ and $$\frac{1}{\tan}$$ are not the same) to use $$(0, \pi)$$ instead.

## Definition: Arccotangent

$$\operatorname{arccot} \coloneqq x \longmapsto \theta \mid x = \cot \theta, \theta \in (0, \pi) \; \forall x \in \mathbb{R}.$$

---

Now there's really only one thing left for us to do, which is to work out the derivatives of all $$6$$ trigonometric functions and all $$6$$ inverse trigonometric functions. We've already done $$\sin$$ and $$\cos$$, of course.

## Theorem: Derivative of Tangent

$$\frac{d\tan x}{dx} = \sec^2 x \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Tangent](/trigonometry#definition-tangent), [Quotient Rule](/differential-calculus#theorem-quotient-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine), [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity), and [Definition: Secant](/trigonometry#definition-secant),

$$\frac{d\tan x}{dx} = \frac{d}{dx} \frac{\sin x}{\cos x} = \frac{\cos x \cos x - \sin x (-\sin x)}{\cos^2 x} = \frac{1}{\cos^2 x} = \sec^2 x \; \forall x \mid \cos x \neq 0.$$

For $$x \mid \cos x = 0$$, $$\tan x$$ is undefined, and thus its derivative is also (by [Definition: Derivative](/differential-calculus#definition-derivative)). However, $$\sec^2 x$$ is also undefined for such $$x$$. Therefore

$$\frac{d\tan x}{dx} = \sec^2 x \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Secant

$$\frac{d\sec x}{dx} = \sec x \tan x \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Secant](/trigonometry#definition-secant), [Quotient Rule](/differential-calculus#theorem-quotient-rule), [Constant Rule](/differential-calculus#theorem-constant-rule), [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine), and [Definition: Tangent](/trigonometry#definition-tangent),

$$\frac{d\sec x}{dx} = \frac{d}{dx} \frac{1}{\cos x} = \frac{\cos x \cdot 0 - 1 \cdot (-\sin x)}{\cos^2 x} = \frac{1}{\cos x} \cdot \frac{\sin x}{\cos x} = \sec x \tan x \; \forall x \mid \cos x \neq 0.$$

For $$x \mid \cos x = 0$$, $$\sec x$$ is undefined, and thus its derivative is also (by [Definition: Derivative](/differential-calculus#definition-derivative)). However, $$\sec x \tan x$$ is also undefined for such $$x$$. Therefore

$$\frac{d\sec x}{dx} = \sec x \tan x \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Cosecant

$$\frac{d\csc x}{dx} = -\csc x \cot x \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Cosecant](/trigonometry#definition-cosecant), [Quotient Rule](/differential-calculus#theorem-quotient-rule), [Constant Rule](/differential-calculus#theorem-constant-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), and [Definition: Cotangent](/trigonometry#definition-cotangent),

$$\frac{d\csc x}{dx} = \frac{d}{dx} \frac{1}{\sin x} = \frac{\sin x \cdot 0 - 1 \cdot \cos x}{\sin^2 x} = \frac{-1}{\sin x} \cdot \frac{\cos x}{\sin x} = -\csc x \cot x \; \forall x \mid \sin x \neq 0.$$

For $$x \mid \sin x = 0$$, $$\csc x$$ is undefined, and thus its derivative is also (by [Definition: Derivative](/differential-calculus#definition-derivative)). However, $$-\csc x \cot x$$ is also undefined for such $$x$$. Therefore

$$\frac{d\csc x}{dx} = -\csc x \cot x \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Cotangent

$$\frac{d\cot x}{dx} = -\csc^2 x \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Cotangent](/trigonometry#definition-cotangent), [Quotient Rule](/differential-calculus#theorem-quotient-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine), [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity), and [Definition: Cosecant](/trigonometry#definition-cosecant),

$$\frac{d\cot x}{dx} = \frac{d}{dx} \frac{\cos x}{\sin x} = \frac{\sin x (-\sin x) - \cos x \cos x}{\sin^2 x} = \frac{-1}{\sin^2 x} = -\csc^2 x \; \forall x \mid \sin x \neq 0.$$

For $$x \mid \sin x = 0$$, $$\cot x$$ is undefined, and thus its derivative is also (by [Definition: Derivative](/differential-calculus#definition-derivative)). However, $$-\csc^2 x$$ is also undefined for such $$x$$. Therefore

$$\frac{d\cot x}{dx} = -\csc^2 x \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Arcsine

$$\frac{d\arcsin x}{dx} = \frac{1}{\sqrt{1 - x^2}} \; \forall x \in [-1, 1].$$

**Proof.** By [Definition: Arcsine](/trigonometry#definition-arcsine), $$\arcsin x$$ is only defined for $$x \in [-1, 1]$$ and is by [Definition: Differentiable](/differential-calculus#definition-differentiable) not differentiable for $$x = \pm 1$$ since at both $$x$$-values one side of the limit fails to exist. Now, by [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule), [Derivative of Sine](/trigonometry#theorem-derivative-of-sine), and [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity),

$$\left.\frac{d\arcsin y}{dy}\right\rvert_{\sin x} = \frac{1}{\cos x} \; \forall x \in \left(-\frac{\pi}{2}, \frac{\pi}{2} \right) \Longrightarrow \frac{d\arcsin x}{dx} = \frac{1}{\cos(\arcsin x)} = \frac{1}{\sqrt{\cos^2(\arcsin x)}} = \frac{1}{\sqrt{1 - \sin^2(\arcsin x)}} = \frac{1}{\sqrt{1 - x^2}} \; \forall x \in (-1, 1).$$

However, $$\frac{1}{\sqrt{1 - x^2}}$$ is undefined for $$x = \pm 1$$, so we may still write 

$$\frac{d\arcsin x}{dx} = \frac{1}{\sqrt{1 - x^2}} \; \forall x \in [-1, 1]. \text{ } \Box$$

---

Also notice that we couldn't define a derivative on for $$\arcsin$$ on the edges of its domain even if we used a one-sided limit to differentiate it: $$\sin x$$ flattens out (has a derivative of $$0$$) for $$x = \pm \frac{\pi}{2}$$, so the derivative of $$\arcsin x$$ for $$x = \pm 1$$ would be infinite (almost no change in $$y$$ per change in $$x$$ means almost infinite change in $$x$$ per change in $$y$$).

## Theorem: Derivative of Arccosine

$$\frac{d\arccos x}{dx} = \frac{-1}{\sqrt{1 - x^2}} \; \forall x \in [-1, 1].$$

**Proof.** By [Definition: Arccosine](/trigonometry#definition-arccosine), $$\arccos x$$ is only defined for $$x \in [-1, 1]$$ and is by [Definition: Differentiable](/differential-calculus#definition-differentiable) not differentiable for $$x = \pm 1$$ since at both $$x$$-values one side of the limit fails to exist. Now, by [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule), [Derivative of Cosine](/trigonometry#theorem-derivative-of-cosine), and [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity),

$$\left.\frac{d\arccos y}{dy}\right\rvert_{\cos x} = \frac{-1}{\sin x} \; \forall x \in (0, \pi) \Longrightarrow \frac{d\arccos x}{dx} = \frac{-1}{\sin(\arccos x)} = \frac{-1}{\sqrt{\sin^2(\arccos x)}} = \frac{-1}{\sqrt{1 - \cos^2(\arccos x)}} = \frac{-1}{\sqrt{1 - x^2}} \; \forall x \in (-1, 1).$$

However, $$\frac{-1}{\sqrt{1 - x^2}}$$ is undefined for $$x = \pm 1$$, so we may still write 

$$\frac{d\arccos x}{dx} = \frac{-1}{\sqrt{1 - x^2}} \; \forall x \in [-1, 1]. \text{ } \Box$$

---

Same deal on the boundaries with $$\arccos$$ as with $$\arcsin$$.

## Theorem: Derivative of Arctangent

$$\frac{d\arctan x}{dx} = \frac{1}{1 + x^2} \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Arctangent](/trigonometry#definition-arctangent), [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule), and [Derivative of Tangent](/trigonometry#theorem-derivative-of-tangent),

$$\left.\frac{d\arctan y}{dy}\right\rvert_{\tan x} = \frac{1}{\sec^2 x} \; \forall x \in \left(-\frac{\pi}{2}, \frac{\pi}{2} \right) \Longrightarrow \frac{d\arctan x}{dx} = \frac{1}{\sec^2(\arctan x)} \; \forall x \in \mathbb{R}.$$

But by [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity), [Definition: Tangent](/trigonometry#definition-tangent), and [Definition: Secant](/trigonometry#definition-secant),

$$\cos^2 x + \sin^2 x = 1 \; \forall x \in \mathbb{R} \Longrightarrow 1 + \tan^2 x = \sec^2 x \; \forall x \in \mathbb{R}.$$

Therefore

$$\frac{d\arctan x}{dx} = \frac{1}{1 + \tan^2(\arctan x)} = \frac{1}{1 + x^2} \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Arccotangent

$$\frac{d\operatorname{arccot} x}{dx} = \frac{-1}{1 + x^2} \; \forall x \in \mathbb{R}.$$

**Proof.** By [Definition: Arccotangent](/trigonometry#definition-arctangent), [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule), and [Derivative of Cotangent](/trigonometry#theorem-derivative-of-cotangent),

$$\left.\frac{d\operatorname{arccot} y}{dy}\right\rvert_{\cot x} = \frac{-1}{\csc^2 x} \; \forall x \in (0, \pi) \Longrightarrow \frac{d\operatorname{arccot} x}{dx} = \frac{-1}{\csc^2(\operatorname{arccot} x)} \; \forall x \in \mathbb{R}.$$

But by [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity), [Definition: Cotangent](/trigonometry#definition-cotangent), and [Definition: Cosecant](/trigonometry#definition-cosecant),

$$\cos^2 x + \sin^2 x = 1 \; \forall x \in \mathbb{R} \Longrightarrow \cot^2 x + 1 = \csc^2 x \; \forall x \in \mathbb{R}.$$

Therefore

$$\frac{d\operatorname{arccot} x}{dx} = \frac{-1}{1 + \cot^2(\operatorname{arccot} x)} = \frac{-1}{1 + x^2} \; \forall x \in \mathbb{R}. \text{ } \Box$$

## Theorem: Derivative of Arcsecant

$$\frac{d\operatorname{arcsec} x}{dx} = \frac{1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1] \cup [1, \infty).$$

**Proof.** By [Definition: Arcsecant](/trigonometry#definition-arcsecant), $$\operatorname{arcsec} x$$ is only defined for $$x \in (-\infty, -1] \cup [1, \infty)$$ and is by [Definition: Differentiable](/differential-calculus#definition-differentiable) not differentiable for $$x = \pm 1$$ since at both $$x$$-values one side of the limit fails to exist. Now, by [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule) and [Derivative of Secant](/trigonometry#theorem-derivative-of-secant),

$$\left.\frac{d\operatorname{arcsec} y}{dy}\right\rvert_{\sec x} = \frac{1}{\sec x \tan x} \; \forall x \in (0, \pi) \neq \frac{\pi}{2} \Longrightarrow \frac{d\operatorname{arcsec} x}{dx} = \frac{1}{\sec(\operatorname{arcsec} x) \tan(\operatorname{arcsec} x)} = \frac{1}{x \tan(\operatorname{arcsec} x)} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

Now, by [Definition: Tangent](/trigonometry#definition-tangent),

$$x \in (-\infty, -1] \Longrightarrow \tan(\operatorname{arcsec} x) \leq 0,$$

$$x \in [1, \infty) \Longrightarrow \tan(\operatorname{arcsec} x) \geq 0.$$

Therefore

$$x \tan(\operatorname{arcsec} x) \geq 0 \; \forall x \in (-\infty, -1] \cup [1, \infty),$$

and thus

$$\frac{d\operatorname{arcsec} x}{dx} = \frac{1}{\lvert x \tan(\operatorname{arcsec} x) \rvert} = \frac{1}{\lvert x \rvert \sqrt{\tan^2(\operatorname{arcsec} x)}} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

But by [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity) and [Definition: Secant](/trigonometry#definition-secant),

$$\cos^2 x + \sin^2 x = 1 \; \forall x \in \mathbb{R} \Longrightarrow 1 + \tan^2 x = \sec^2 x \; \forall x \in \mathbb{R} \Longrightarrow \tan^2 x = \sec^2 x - 1 \; \forall x \in \mathbb{R}.$$

Therefore

$$\frac{d\operatorname{arcsec} x}{dx} = \frac{1}{\lvert x \rvert \sqrt{\sec^2(\operatorname{arcsec} x) - 1}} = \frac{1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

However, for $$x = \pm 1$$, $$\frac{1}{\lvert x \rvert \sqrt{x^2 - 1}}$$ is undefined, so we may still write 

$$\frac{d\operatorname{arcsec} x}{dx} = \frac{1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1] \cup [1, \infty). \text{ } \Box$$

---

Notice that like with $$\arcsin$$ and $$\arccos$$, because $$\sec x$$ "stalls out" at $$x = 0$$ and $$x = \pi$$ (its derivative, $$\sec x \tan x$$, is $$0$$ for both of these values), we couldn't define $$\left.\frac{d\operatorname{arcsec} x}{dx}\right\rvert_{1}$$ or $$\left.\frac{d\operatorname{arcsec} x}{dx}\right\rvert_{-1}$$ even if we wanted to as we would get an infinite slope.

## Theorem: Derivative of Arccosecant

$$\frac{d\operatorname{arccsc} x}{dx} = \frac{-1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1] \cup [1, \infty).$$

**Proof.** By [Definition: Arccosecant](/trigonometry#definition-arccosecant), $$\operatorname{arccsc} x$$ is only defined for $$x \in (-\infty, -1] \cup [1, \infty)$$ and is by [Definition: Differentiable](/differential-calculus#definition-differentiable) not differentiable for $$x = \pm 1$$ since at both $$x$$-values one side of the limit fails to exist. Now, by [Inverse Function Rule](/differential-calculus#theorem-inverse-function-rule) and [Derivative of Cosecant](/trigonometry#theorem-derivative-of-cosecant),

$$\left.\frac{d\operatorname{arccsc} y}{dy}\right\rvert_{\csc x} = \frac{-1}{\csc x \cot x} \; \forall x \in \left(-\frac{\pi}{2}, \frac{\pi}{2} \right) \neq 0 \Longrightarrow \frac{d\operatorname{arccsc} x}{dx} = \frac{-1}{\csc(\operatorname{arccsc} x) \cot(\operatorname{arccsc} x)} = \frac{-1}{x \cot(\operatorname{arccsc} x)} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

Now, by [Definition: Cotangent](/trigonometry#definition-cotangent),

$$x \in (-\infty, -1] \Longrightarrow \cot(\operatorname{arccsc} x) \leq 0,$$

$$x \in [1, \infty) \Longrightarrow \cot(\operatorname{arccsc} x) \geq 0.$$

Therefore

$$x \cot(\operatorname{arccsc} x) \geq 0 \; \forall x \in (-\infty, -1] \cup [1, \infty),$$

and thus

$$\frac{d\operatorname{arccsc} x}{dx} = \frac{-1}{\lvert x \cot(\operatorname{arccsc} x) \rvert} = \frac{-1}{\lvert x \rvert \sqrt{\cot^2(\operatorname{arccsc} x)}} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

But by [Pythagorean Trigonometric Identity](/trigonometry#theorem-pythagorean-trigonometric-identity) and [Definition: Cosecant](/trigonometry#definition-cosecant),

$$\cos^2 x + \sin^2 x = 1 \; \forall x \in \mathbb{R} \Longrightarrow \cot^2 x + 1 = \csc^2 x \; \forall x \in \mathbb{R} \Longrightarrow \cot^2 x = \csc^2 x - 1 \; \forall x \in \mathbb{R}.$$

Therefore

$$\frac{d\operatorname{arccsc} x}{dx} = \frac{-1}{\lvert x \rvert \sqrt{\csc^2(\operatorname{arccsc} x) - 1}} = \frac{-1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1) \cup (1, \infty).$$

However, for $$x = \pm 1$$, $$\frac{-1}{\lvert x \rvert \sqrt{x^2 - 1}}$$ is undefined, so we may still write 

$$\frac{d\operatorname{arccsc} x}{dx} = \frac{-1}{\lvert x \rvert \sqrt{x^2 - 1}} \; \forall x \in (-\infty, -1] \cup [1, \infty). \text{ } \Box$$

---

Again, $$\frac{d\csc x}{dx} = -\csc x \cot x$$ is $$0$$ for $$x = \pm \frac{\pi}{2}$$, so we couldn't define $$\left.\frac{d\operatorname{arccsc} x}{dx}\right\rvert_{1}$$ or $$\left.\frac{d\operatorname{arccsc} x}{dx}\right\rvert_{-1}$$ even if we wanted to.

And at last we've exhausted most of the common stuff we can do using trigonometry and differential calculus! But we're not even close to done with calculus in general. Coming up next is integral calculus.
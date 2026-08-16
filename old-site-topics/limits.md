---
title: Limits*
permalink: /old-site-topics/limits
parent: Old Site Topics*
nav_order: 2
---

# Limits

Consider a function like $$f \colon x \longmapsto x \cdot \frac{x - 1}{x - 1} \; \forall x \in \mathbb{R}.$$ This function looks like $$x \longmapsto x$$ everywhere except at $$x = 1$$, where there's a hole in the graph ($$\frac{0}{0}$$ is undefined). Yet, it seems like we should still be able to assign the graph a value at $$x = 1$$ in some sense: Hole notwithstanding, all signs point to $$f(1) = 1.$$ Here's how we do that: by letting the graph point the way.

Informally, start somewhere the graph is well defined (at $$x = 2$$, say) and trace along the graph all the way over to *just*—think infinitely close—short of $$x = 1.$$ Then, do it again, but coming from the other side (start, say, at $$x = 0$$). This will yield two potential "pseudo-values" for $$f(1)$$ with infinitely small (i.e., zero) error. As long as these two agree, you have a well-defined "pseudo-value" for $$f(1)$$, which we call the *limit of* $$f(x)$$ *as* $$x$$ *tends to* $$1$$,

$$\lim_{x \to 1} f(x).$$

We should formalize that, of course. First of all, where you start on either side of $$x = 1$$ doesn't matter, nor does the speed with which you approach $$1$$, the order you make the two approaches in (i.e., whether you come from the left or the right first), or if you make the approaches separately. So, without loss of generality, we can consider a shrinking range $$(1 - \delta, 1 + \delta)$$ of "radius" $$\delta > 0$$ centered at $$1.$$ Then, if the limit equals $$1$$, as $$\delta$$ shrinks the range of corresponding $$f$$-values gets arbitrarily small around $$1$$, so that for any $$\epsilon > 0$$ we can always find a $$\delta > 0$$ such that $$f(x) \in (1 - \epsilon, 1 + \epsilon)$$ for all $$x \neq 1$$ in the range $$(1 - \delta, 1 + \delta)$$. (Notice that because $$f$$ is a function, $$1$$ is the only limit value which satisfies this.) That's a fully well-defined statement! We'll solidify it as the formal definition of a limit.

## Definition: Limit

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, a \in \mathbb{R}.$$ Then

$$\lim_{x \to a} f(x)$$

(read as "the limit of $$f(x)$$ as $$x$$ tends to $$a$$"), if it exists, is defined as the unique value $$L \in \mathbb{R}$$ such that

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies f(x) \in (L - \epsilon, L + \epsilon) \right],$$

$$\lim_{x \to \infty} f(x),$$

if it exists, is defined as the unique value $$M \in \mathbb{R}$$ such that

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x > \delta \implies f(x) \in (M - \epsilon, M + \epsilon) \right],$$

and 

$$\lim_{x \to -\infty} f(x),$$

if it exists, is defined as the unique value $$K \in \mathbb{R}$$ such that

$$\forall \epsilon > 0 \colon \exists \delta < 0 \colon \left[ x < \delta \implies f(x) \in (K - \epsilon, K + \epsilon) \right].$$

---

The idea of approaching from both sides and having those *one-sided limits* agree is not lost in this definition.

## Definition: One-Sided Limit

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, a \in \mathbb{R}.$$ Then

$$\lim_{x \to a^-} f(x)$$

(read as "the limit of $$f(x)$$ as $$x$$ tends to $$a$$ from the left"), if it exists, is defined as the unique value $$L \in \mathbb{R}$$ such that

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a) \implies f(x) \in (L - \epsilon, L + \epsilon) \right],$$

and

$$\lim_{x \to a^+} f(x)$$

(read as "the limit of $$f(x)$$ as $$x$$ tends to $$a$$ from the right"), if it exists, is defined as the unique value $$M \in \mathbb{R}$$ such that

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a, a + \delta) \implies f(x) \in (M - \epsilon, M + \epsilon) \right].$$

## Theorem: Limit Exists Iff One-Sided Limits Agree

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}, L \in \mathbb{R}$$. Then

$$\lim_{x \to a} f(x) = L \Longleftrightarrow \lim_{x \to a^-} f(x) = L = \lim_{x \to a^+} f(x).$$

**Proof.** 

$$x \in (a - \delta, a + \delta) \neq x \Longleftrightarrow x \in (a - \delta, a) \cup (a, a + \delta) \Longleftrightarrow x \in (a - \delta, a) \text{ or } x \in (a, a + \delta).$$

Therefore

$$\lim_{x \to a} f(x) = L \Longleftrightarrow \forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a) \cup (a, a + \delta) \implies f(x) \in (L - \epsilon, L + \epsilon) \right] \Longleftrightarrow \forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a) \text{ or } x \in (a, a + \delta) \implies f(x) \in (L - \epsilon, L + \epsilon) \right] \Longleftrightarrow \lim_{x \to a^-} f(x) = L = \lim_{x \to a^+} f(x). \text{ } \Box$$

---

Having now defined a limit, we have a very nice way of defining what it means for a function $$f(x) \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}$$ to be continuous at $$x = a$$: $$f(a)$$ exists, and arbitrarily small variations in $$f(x)$$ around $$f(a)$$ are always possible via variations of $$x$$ around $$a$$.

## Definition: Continuous

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then $$f$$ (and $$f(x)$$) are called continuous at $$a$$ iff

$$\lim_{x \to a} f(x) = f(a),$$

continuous at $$a$$ from the left iff

$$\lim_{x \to a^-} f(x) = f(a),$$

and continuous at $$a$$ from the right iff

$$\lim_{x \to a^+} f(x) = f(a).$$

---

Now let's prove a few results about manipulating limits in order to make life much easier when we're actually computing them. These are pretty intuitive, but it's good practice not to jump to conclusions.

## Theorem: Limit of Constant Is Constant

Let $$a, c \in \mathbb{R}.$$ Then 

$$\lim_{x \to a} c = c.$$

**Proof.**

$$\forall \epsilon > 0, \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \implies \left.c\right\rvert_x = c \in (c - \epsilon, c + \epsilon) \right].$$

Therefore, by [Definition: Limit](/limits#definition-limit),

$$\lim_{x \to a} c = c. \text{ } \Box$$

## Theorem: Limit of Variable Is Approached Value

Let $$a \in \mathbb{R}.$$ Then 

$$\lim_{x \to a} x = a.$$

**Proof.** Let $$\delta = \epsilon.$$ Then

$$\forall \epsilon > 0 \colon \left[ x \in (a - \delta, a + \delta) \implies x \in (a - \epsilon, a + \epsilon) \right].$$

Therefore, by [Definition: Limit](/limits#definition-limit),

$$\lim_{x \to a} x = a. \text{ } \Box$$

## Theorem: Limits and Constant Factors Commute

Let $$a, c, L \in \mathbb{R}.$$ Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} f(x) = L.$$ Then 

$$\lim_{x \to a} cf(x) = c \lim_{x \to a} f(x).$$

**Proof.** In the case where $$c = 0$$, by [Limit of Constant Is Constant](/limits#theorem-limit-of-constant-is-constant),

$$\lim_{x \to a} cf(x) = \lim_{x \to a} 0 = 0 = 0 \cdot L = c \lim_{x \to a} f(x).$$

If $$c \neq 0$$:

$$\lim_{x \to a} f(x) = L \implies \forall \epsilon' > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies f(x) \in (L - \epsilon', L + \epsilon') \implies cf(x) \in (c(L - \epsilon'), c(L + \epsilon')) = (cL - c\epsilon', cL + c\epsilon') \right].$$

If $$c < 0$$, this is technically improper notation; we should be writing $$(cL + c\epsilon', cL - c\epsilon').$$ But minor notational inconsistency notwithstanding, if we now let $$\epsilon = \pm c\epsilon'$$ (as appropriate such that $$\epsilon > 0$$), we have

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies cf(x) \in (cL - \epsilon, cL + \epsilon) \right].$$

$$\lim_{x \to a} cf(x) = cL = c \lim_{x \to a} f(x)$$

by [Definition: Limit](/limits#definition-limit). $$\Box$$

## Theorem: Limit of Sum Is Sum of Limits

Let $$a, L, M \in \mathbb{R}.$$ Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} f(x) = L.$$ Let $$g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} g(x) = M.$$ Then

$$\lim_{x \to a} [f(x) \pm g(x)] = \lim_{x \to a} f(x) \pm \lim_{x \to a} g(x).$$

**Proof.** Let's first prove that

$$\lim_{x \to a} [f(x) + g(x)] = \lim_{x \to a} f(x) + \lim_{x \to a} g(x).$$

Because both limits on the right-hand side exist, we know that

$$\forall \epsilon' > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies f(x) \in (L - \epsilon', L + \epsilon'), g(x) \in (M - \epsilon', M + \epsilon') \implies f(x) + g(x) \in (L + M - 2\epsilon', L + M + 2\epsilon') \right].$$

If we then let $$\epsilon = 2\epsilon'$$, it follows that

$$\lim_{x \to a} [f(x) + g(x)] = L + M = \lim_{x \to a} f(x) + \lim_{x \to a} g(x)$$

by [Definition: Limit](/limits#definition-limit). The $$f - g$$ case then follows by [Limits and Constant Factors Commute](/limits#theorem-limits-and-constant-factors-commute):

$$\lim_{x \to a} [f(x) - g(x)] = \lim_{x \to a} [f(x) + (- g(x))] = \lim_{x \to a} f(x) + \lim_{x \to a} - g(x) = \lim_{x \to a} f(x) + -\lim_{x \to a} g(x) = \lim_{x \to a} f(x) - \lim_{x \to a} g(x). \text{ } \Box$$

## Theorem: Limit of Product Is Product of Limits

Let $$a, L, M \in \mathbb{R}.$$ Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} f(x) = L.$$ Let $$g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} g(x) = M.$$ Then

$$\lim_{x \to a} [f(x)g(x)] = \lim_{x \to a} f(x) \lim_{x \to a} g(x).$$

**Proof.** Using [Limit of Constant Is Constant](/limits#theorem-limit-of-constant-is-constant) and [Limit of Sum Is Sum of Limits](/limits#theorem-limit-of-sum-is-sum-of-limits), we can show that

$$\lim_{x \to a} f(x) - L = \lim_{x \to a} f(x) - \lim_{x \to a} L = L - L = 0,$$

$$\lim_{x \to a} g(x) - M = \lim_{x \to a} g(x) - \lim_{x \to a} M = M - M = 0.$$

Therefore

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies f(x) - L, g(x) - L \in (-\sqrt\epsilon, \sqrt\epsilon) \implies (f(x) - L)(g(x) - M) \in (-\epsilon, \epsilon) \right],$$

and thus we have that

$$\lim_{x \to a} (f(x) - L)(g(x) - M) = 0.$$

If we then expand the product and apply [Limit of Constant Is Constant](/limits#theorem-limit-of-constant-is-constant), [Limits and Constant Factors Commute](/limits#theorem-limits-and-constant-factors-commute), and [Limit of Sum Is Sum of Limits](/limits#theorem-limit-of-sum-is-sum-of-limits):

$$\lim_{x \to a} (f(x) - L)(g(x) - M) = \lim_{x \to a} f(x)g(x) - Mf(x) - Lg(x) + LM = \lim_{x \to a} f(x)g(x) + \lim_{x \to a} -Mf(x) + \lim_{x \to a} - Lg(x) + \lim_{x \to a} LM = \lim_{x \to a} f(x)g(x) + -ML -LM + LM = 0 \implies \lim_{x \to a} f(x)g(x) = LM = \lim_{x \to a} f(x) \lim_{x \to a} g(x). \text{ } \Box$$

## Theorem: Limit of Ratio Is Ratio of Limits

Let $$a, L, M \in \mathbb{R} \mid M \neq 0.$$ Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} f(x) = L.$$ Let $$g \colon Y \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} g(x) = M.$$ Then

$$\lim_{x \to a} \frac{f(x)}{g(x)} = \frac{\underset{x \to a}{\lim} f(x)}{\underset{x \to a}{\lim} g(x)}.$$

**Proof.** Using the fact that $$\underset{x \to a}{\lim} g(x) = M$$, we have that

$$\exists \delta_1 > 0 \colon \left[ x \in (a - \delta_1, a + \delta_1) \neq a \implies g(x) \in \left( \frac{M}{2}, \frac{3M}{2} \right) \implies \lvert g(x) \rvert > \frac{\lvert M \rvert}{2} \implies \frac{1}{\lvert g(x) \rvert} < \frac{2}{\lvert M \rvert} \right],$$

$$\forall \epsilon > 0 \colon \exists \delta_2 > 0 \colon \left[ x \in (a - \delta_2, a + \delta_2) \neq a \implies g(x) \in \left( M - \frac{M^2}{2} \epsilon, M + \frac{M^2}{2} \epsilon \right) \implies \lvert g(x) - M\rvert < \frac{M^2}{2} \epsilon \right].$$

Note the slightly improper notation: If $$M < 0$$ then the interval on the first line should be $$\left( \frac{3M}{2}, \frac{M}{2} \right)$$, not the other way around. Regardless, we can use the above two results to now show the following:

$$\forall \epsilon > 0 \colon \exists \delta = \operatorname{min}(\delta_1, \delta_2) > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies \left\lvert \frac{1}{g(x)} - \frac{1}{M} \right\rvert = \left\lvert \frac{M - g(x)}{Mg(x)} \right\rvert = \frac{1}{\lvert M \rvert} \frac{1}{\lvert g(x) \rvert} \lvert g(x) - M \rvert < \frac{1}{\lvert M \rvert} \frac{2}{\lvert M \rvert} \lvert g(x) - M \rvert < \frac{1}{\lvert M \rvert} \frac{2}{\lvert M \rvert} \frac{M^2}{2} \epsilon = \epsilon \Longleftrightarrow \frac{1}{g(x)} \in \left( \frac{1}{M} - \epsilon, \frac{1}{M} + \epsilon \right) \right].$$

Thus, by [Definition: Limit](/limits#definition-limit), 

$$\lim_{x \to a} \frac{1}{g(x)} = \frac{1}{M},$$

and so from [Limit of Product Is Product of Limits](/limits#theorem-limit-of-product-is-product-of-limits), it follows that 

$$\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} f(x) \frac{1}{g(x)} = \lim_{x \to a} f(x) \lim_{x \to a} \frac{1}{g(x)} = L \cdot \frac{1}{M} = \frac{L}{M} = \frac{\underset{x \to a}{\lim} f(x)}{\underset{x \to a}{\lim} g(x)}. \text{ } \Box$$

## Limit Change of Variables Theorem

Let $$a, b, L \in \mathbb{R}$$. Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R} \mid \underset{x \to a}{\lim} f(x) = L$$. Then if

$$\lim_{y \to b} x = a$$

and

$$\exists r > 0 \colon \left[ y \in (b - r, b + r) \neq b \implies x \neq a \right]$$

then

$$\lim_{y \to b} f(x) = L.$$

**Proof.**

$$\forall \delta > 0 \colon \exists \gamma > 0 \colon \left[ y \in (b - \gamma, b + \gamma) \neq b \implies x \in (a - \delta, a + \delta) \neq a \right]$$

and

$$\forall \epsilon > 0 \colon \exists \delta > 0 \colon \left[ x \in (a - \delta, a + \delta) \neq a \implies f(x) \in (L - \epsilon, L + \epsilon) \right].$$

Therefore

$$\forall \epsilon > 0 \colon \exists \gamma > 0 \colon \left[ y \in (b - \gamma, b + \gamma) \neq b \implies f(x) \in (L - \epsilon, L + \epsilon) \right].$$

$$\lim_{y \to b} f(x) = L$$

by [Definition: Limit](/limits#definition-limit). $$\Box$$

---

To solidify some results that we're going to want to use [later on](/differential-calculus), let's also go ahead and prove some results that we'd expect a continuous function to satisfy.

## Definition: Bounded

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then $$f$$ is called bounded on some $$U \subseteq X$$ iff

$$\exists u,v \in \mathbb{R} \colon \forall x \in U \colon u \leq f(x) \leq v.$$

$$u$$ is then called a lower bound of $$f$$ on $$U$$ and $$v$$ is then called an upper bound of $$f$$ on $$U$$.

## Boundedness Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then if $$f$$ is continuous on $$(a,b)$$, continuous from the right at $$a$$, and continuous from the left at $$b$$ for some $$a,b \in \mathbb{R}$$, then $$f$$ is bounded on $$[a,b]$$.

**Proof.** Let

$$B = \{p \in [a,b] \mid f \text{ is bounded on } [a,p]\}.$$

$$a \in B.$$

$$\exists c > a \colon c \in B \implies [a, c] \subseteq B.$$

$$f$$ is continuous from the right at $$a$$. Therefore

$$\exists \delta > 0 \colon \left[ x \in [a, a + \delta) \implies f(x) \in (f(a) - 1, f(a) + 1) \right].$$

Hence $$B$$ is an interval of nonzero length, i.e.,

$$\exists s \in (a, b] \colon \left( B = [a, s) \text{ or } B = [a,s] \right).$$

Suppose $$s < b$$. Then $$f$$ is continuous at $$s$$ and so

$$\exists \delta > 0 \colon \left[ x \in (s - \delta, s + \delta) \subseteq (a, b) \implies f(x) \in (f(s) - 1, f(s) + 1) \right],$$

which implies that $$f$$ is bounded on $$[a, s + \delta) \subseteq [a, b)$$, contradicting $$B = [a, s) \text{ or } B = [a,s]$$. Therefore

$$s = b \implies B = [a, b) \text{ or } B = [a,b].$$

$$f$$ is continuous from the left at $$b$$. Therefore

$$\exists \delta > 0 \colon \left[ x \in (b - \delta, b] \implies f(x) \in (f(b) - 1, f(b) + 1) \right].$$

$$f$$ is bounded on $$[a, b]$$. $$\Box$$

## Extreme Value Theorem

Let $$f \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Then if $$f$$ is continuous on $$(a,b)$$, continuous from the right at $$a$$, and continuous from the left at $$b$$ for some $$a,b \in \mathbb{R}$$, then $$f$$ attains a maximum value and a minimum value on $$[a,b]$$.

**Proof.** $$f$$ is bounded on $$[a,b]$$ by the [Boundedness Theorem](/limits#boundedness-theorem) and thus has an upper bound. We will first show that it attains its least upper bound. 

Let $$M$$ be the least upper bound of $$f$$ on $$[a,b]$$. Then $$\forall x \in [a,b] \colon f(x) \leq M$$. Suppose $$\forall x \in [a,b] \colon f(x) < M$$. Then 

$$\frac{1}{M - f(x)}$$

is greater than zero for all $$x \in [a,b]$$ and continuous on $$(a,b)$$ by [Limit of Ratio is Ratio of Limits](/limits#theorem-limit-of-ratio-is-ratio-of-limits), [Limit of Constant Is Constant](/limits#theorem-limit-of-constant-is-constant), [Limit of Sum Is Sum of Limits](/limits#theorem-limit-of-sum-is-sum-of-limits), and the continuity of $$f$$ on $$(a,b)$$, and it is continuous from the right at $$a$$ and from the left at $$b$$ for the same reasons. It is thus bounded by the [Boundedness Theorem](/limits#boundedness-theorem) and so

$$\exists K > 0 \colon \forall x \in [a,b] \colon \left( \frac{1}{M - f(x)} \leq K \implies f(x) \leq M - \frac{1}{K} \right),$$

contradicting the assumption that $$M$$ is the least upper bound of $$f$$ on $$[a,b]$$. Thus,

$$\exists c \in [a,b] \colon f(c) = M,$$

i.e., $$f$$ attains its least upper bound. By [Limits and Constant Factors Commute](/limits#theorem-limits-and-constant-factors-commute), we can then apply this result to $$-f$$, meaning $$f$$ attains its greatest lower bound on $$[a,b]$$ (the least upper bound of $$-f$$ is the greatest lower bound of $$f$$). $$\Box$$
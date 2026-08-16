---
title: Average Rates of Change*
permalink: /old-site-topics/average-rates-of-change
parent: Old Site Topics*
nav_order: 1
---

# Average Rates of Change

Let $$f(x) \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Let $$\exists a, b \in \mathbb{R} \mid a < b, [a,b] \subseteq X.$$ Suppose I want to quantify how much $$f$$ increases, on average, per unit change in $$x$$ over the interval $$[a,b]$$.

How would we do that? Clearly, we'd want it to be a ratio between change in $$f$$ and change in $$x$$, so we know that much. But what does it mean for this ratio to be the *average* rate of change?

It means that, if $$f$$ starts at $$(a, f(a))$$ and increases at a constant rate of $$m$$ ($$m$$ being its average rate of change on $$[a,b]$$) until reaching $$x = b$$, the end result should be the same as if we had just traced the graph until reaching $$x = b$$. That is, we should end at $$(b, f(b)).$$ Restating that in more mathematical language:

$$f(a) + m(b - a) = f(b),$$

where we multiply $$m$$ by the change in $$x$$ from $$a$$ to $$b$$ to get the total change in $$f$$ from $$a$$ to $$b$$ because

$$\frac{\text{Change in }f}{\text{Change in }x} \cdot \text{Change in }x = \text{Change in }f.$$

So, to arrive at our definition of average rate of change, all we have to do is solve for $$m$$.

## Definition: Average Rate of Change

Let $$f(x) \colon X \subseteq \mathbb{R} \longrightarrow \mathbb{R}.$$ Let $$\exists a, b \in \mathbb{R} \mid a < b, [a,b] \subseteq X.$$ Then the average rate of change (a.k.a. the average *slope*) of $$f$$ on the interval $$[a,b]$$ is defined as

$$\frac{f(b) - f(a)}{b - a}.$$
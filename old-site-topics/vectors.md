---
title: Vectors*
permalink: /old-site-topics/vectors
parent: Old Site Topics*
nav_order: 4
---

# Vectors

There are certain quantities that can't be represented with a real number alone; they also need to include a direction. For example, if you were to walk $$2$$ feet to your left, your displacement couldn't be specified using just the number $$2$$—There are a lot of (infinitely many, in fact) directions you could have walked $$2$$ feet in. That *magnitude*, $$2$$, needs to be accompanied by a direction, "left". This is what vectors are for. (So a vector is essentially an arrow.)

The idea is to impose some Cartesian coordinate system on the area around you with you at the origin. Then, all we need to specify your displacement is the point you end up at (the "tip of the arrow"). From this triple, we ought to be able to reconstruct how far you displaced and in what direction (but—Notice—not where you started).

## Definition: Vector

$$\forall n \in \mathbb{Z} > 0$$, an $$n$$-dimensional vector is any $$v$$ such that

$$v \in \mathbb{R}^n.$$

---

But how will we recover the magnitude of any $$n$$-dimensional vector $$v = (x_1, ..., x_n)$$ given its *components* $$x_1, ..., x_n$$? (This will be something we define rather than prove.) To begin, let's consider the simplest case: $$n = 2$$. Where $$x_1 = a, x_2 = b$$, using [this construction](https://www.mathsisfun.com/geometry/images/pythagoras-proof-square.svg) (and where the sides with lengths $$a$$ and $$b$$ are of course perpendicular to each other), we have

$$c^2 = (a + b)^2 - \frac{1}{2}ab - \frac{1}{2}ab - \frac{1}{2}ab - \frac{1}{2}ab = (a + b)^2 - 2ab = a^2 + 2ab + b^2 - 2ab = a^2 + b^2,$$

so we have that $$v$$ is of magnitude

$$\sqrt{x_1^2 + x_2^2}.$$

In a setting with actual axioms and whatnot where this could properly be called a theorem, this would be the famous Pythagoras's theorem. Anyway, from here, in the $$n = 3$$ case, because each component in question is perpendicular to all others, we may apply the $$n = 2$$ case to $$2$$ of the $$3$$ directions to get that the vector has length $$\sqrt{x_1^2 + x_2^2}$$ in a certain direction and length $$x_3$$ in a perpendicular direction, then apply the $$n = 2$$ case again to arrive at a magnitude of 

$$\sqrt{\left(\sqrt{x_1^2 + x_2^2} \right)^2 + x_3^2} = \sqrt{x_1^2 + x_2^2 + x_3^2}.$$

For the $$n = 4$$ case, in a similar fashion, we may apply the $$n = 3$$ case and then the $$n = 2$$ case to get a magnitude of 

$$\sqrt{x_1^2 + x_2^2 + x_3^2 + x_4^2},$$

and so on, so the magnitude of $$v$$ for any generic $$n \in \mathbb{Z} > 0$$ is

$$\sqrt{x_1^2 + \cdots + x_n^2}.$$

The magnitude of $$v$$ is also called the *norm* of $$v$$ and is denoted $$\lvert v \rvert$$.

## Definition: Norm

$$\forall v = (x_1, ..., x_n) \in \mathbb{R}^n$$ $$\exists n \in \mathbb{Z} > 0$$,

$$\lvert v \rvert \coloneqq \sqrt{x_1^2 + \cdots + x_n^2}.$$

---

As we might have guessed, it makes sense to define that two vectors can be added by just adding their components—A displacement of $$3$$ meters up and $$2$$ meters right followed by a displacement of $$1$$ meter up and $$-1$$ meter right ($$1$$ meter left), e.g., ought to equal a displacement of $$4$$ meters up and $$1$$ meter right.

## Definition: Vector Addition

$$\forall u = (u_1, ..., u_n), v = (v_1, ..., v_n) \in \mathbb{R}^n$$,

$$u \pm v \coloneqq (u_1 \pm v_1, ..., u_n \pm v_n).$$

---

Vector addition can be visualized as [forming a new vector by "connecting tip to tail"](https://en.neurochispas.com/wp-content/uploads/2022/11/Adding-two-vectors-head-to-tail-from-A-to-B-600x432.png). (Sometimes vectors are denoted by letters with arrows over them; hence the notation in the image.)

Similarly, multiplication of a vector by a real number (often called a *scalar* to differentiate it from a vector, although it is technically a $$1$$-dimensional vector) ought to stretch it out by that factor, which ought to be the same as stretching each component by that factor (doubling your displacement means displacing twice as much in each direction, e.g.).

## Definition: Scalar Multiplication

$$\forall a \in \mathbb{R}, v = (v_1, ..., v_n) \in \mathbb{R}^n$$,

$$av \coloneqq (av_1, ..., av_n),$$

$$\frac{v}{a} \coloneqq \frac{1}{a}v.$$

---

This also preserves the idea of repeated addition.

Now, what about the limit of a vector-valued function? It's pretty easy to see that since vectors are $$n$$-tuples, we can't really shrink a range of inputs around a single value and near a single output tuple unless every function in the tuple shrinks to a single output in the process. So the simplest definition is also the most natural.

## Definition: Limit of a Vector-Valued Function

$$\forall f = (f_1,...,f_n) \colon U \longrightarrow \mathbb{R}^n$$ $$\exists f_1,...,f_n \colon U \longrightarrow \mathbb{R}, U \subseteq \mathbb{R}, n \in \mathbb{Z} > 0, c \in \mathbb{R}$$,

$$\lim_{t \to c} f(t) \coloneqq \left(\lim_{t \to c} f_1(t),...,\lim_{t \to c} f_n(t) \right).$$

---

So then to differentiate a vector-valued function, we just need to differentiate each component function.

## Definition: Derivative of a Vector-Valued Function

$$\forall f = (f_1,...,f_n) \colon U \longrightarrow \mathbb{R}^n$$ $$\exists f_1,...,f_n \colon U \longrightarrow \mathbb{R}, U \subseteq \mathbb{R}, n \in \mathbb{Z} > 0$$,

$$\frac{df}{dt} \coloneqq \left(\frac{df_1}{dt},...,\frac{df_n}{dt} \right).$$

---

And that's the essence of vectors! The only other things we might want to define are a handful of physical vector quantities.

## Definition: Distance

If $$x$$ is an object's position vector relative to a certain other object, its distance from that object is defined to be

$$\lvert x \rvert.$$

## Definition: Displacement

If $$x(t)$$ is an object's position vector at a certain time $$t$$, that object's displacement from time $$t_1$$ to time $$t_2$$ is defined to be

$$x(t_2) - x(t_1).$$

## Definition: Velocity

If $$x(t)$$ is an object's position vector at a certain time $$t$$, that object's velocity at time $$t$$ is defined to be

$$\frac{d(x(t))}{dt}.$$

## Definition: Speed

If a $$v$$ is an object's velocity vector, that object's speed is defined to be

$$\lvert v \rvert.$$

---

It's also worth noting that for any $$v = (v_1,v_2) \in \mathbb{R}^2$$, we can rotate $$v$$ $$90$$ degrees counterclockwise by, instead of going right $$v_1$$ and up $$v_2$$, going up $$v_1$$ and left $$v_2$$, so that once rotated $$90$$ degrees counterclockwise, $$v$$ becomes $$(-v_2,v_1)$$, and the opposite for clockwise rotation.
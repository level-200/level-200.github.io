---
title: Groups*
permalink: /groups
---

# Groups

## Definition: Group (Weak Definition)

A *group* is a set $$X$$ together with an associative binary operation $$\begin{cases} X \times X \longrightarrow X\\ (x,y) \longmapsto x \cdot y \end{cases}$$ such that:

$$\exists e \in X \colon \forall x \in X \colon e \cdot x = x,$$

$$\forall x \in X \colon \exists x^{-1} \in X \colon x^{-1} \cdot x = e.$$

**Additional terminology.** $$X$$ is called the group's *underlying set*, the operation is called its *group operation*, $$e$$ is called an *identity element* of the group, and $$x^{-1}$$ is called an *inverse* of $$x$$. In particular, $$y \cdot x$$ and $$x \cdot y$$ are known as *left multiplication* and *right multiplication* of $$x$$ by $$y$$, respectively, $$e$$ is known as a *left identity*, and $$x^{-1}$$ is known as a *left inverse* of $$x$$. You can guess what *right identities* and *right inverses* are.

**Motivation.** A group is meant to represent the set of all *symmetries* of an object, i.e., all actions that could be performed on that object without altering a certain property it has. 

**Remark.** These conditions may seem too weak to fully represent what we'd like. However, we will proceed to show, in the four theorems that follow, that these additional assumptions are in fact already encoded in the above axioms.

## Theorem: All Left Inverses Are Right Inverses

For any group with group operation $$(x,y) \longmapsto x \cdot y$$ and element $$x$$ with left inverse $$x^{-1}$$,

$$x \cdot x^{-1} = x^{-1} \cdot x.$$

**Proof.** Let $$e = x^{-1} \cdot x$$. Let $$(x^{-1})^{-1}$$ be a left inverse of $$x^{-1}$$ such that $$(x^{-1})^{-1} \cdot x^{-1} = e$$.

$$\begin{align}
x \cdot x^{-1} &= (x^{-1})^{-1} \cdot x^{-1} \cdot x \cdot x^{-1} &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\\
&= (x^{-1})^{-1} \cdot e \cdot x^{-1}\\
&= (x^{-1})^{-1} \cdot x^{-1} &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\\
&= e\\
&= x^{-1} \cdot x.
\end{align}$$

## Theorem: All Left Identities Are Right Identities

For any group with underlying set $$X$$, left identity $$e$$, and group operation $$(x,y) \longmapsto x \cdot y$$,

$$\forall x \in X \colon x \cdot e = e \cdot x.$$

**Proof.** Let $$x^{-1}$$ be a left inverse of $$x$$ such that $$x^{-1} \cdot x = e$$.

$$\begin{align}
x \cdot e &= x \cdot x^{-1} \cdot x\\
&= x^{-1} \cdot x \cdot x &&\text{by }\href{/groups#theorem-all-left-inverses-are-right-inverses}{\text{All Left Inverses Are Right Inverses}}\\
&= e \cdot x.
\end{align}$$

## Theorem: Identities Are Unique

All groups have exactly one identity element.

**Proof.** For any group with group operation $$(x,y) \longmapsto x \cdot y$$ and identity elements $$e$$, $$i$$:

$$\begin{align}
e \cdot i &= i &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\text{.}\\
e \cdot i &= i \cdot e &&\text{by }\href{/groups#theorem-all-left-identities-are-right-identities}{\text{All Left Identities Are Right Identities}}\\
&= e &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\text{.}\\
\therefore e &= i.
\end{align}$$

## Theorem: Inverses Are Unique

Any element of a group has exactly one inverse element.

**Proof.** For any group with group operation $$(x,y) \longmapsto x \cdot y$$ and identity element $$e$$, where $$y,z$$ are inverses of the element $$x$$,

$$\begin{align}
y &= e \cdot y &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\\
&= z \cdot x \cdot y &&\text{by }\href{/groups#theorem-identities-are-unique}{\text{Theorem: Identities Are Unique}}\\
&= z \cdot y \cdot x &&\text{by }\href{/groups#theorem-all-left-inverses-are-right-inverses}{\text{All Left Inverses Are Right Inverses}}\\
&= z \cdot e &&\text{by }\href{/groups#theorem-identities-are-unique}{\text{Theorem: Identities Are Unique}}\\
&= e \cdot z &&\text{by }\href{/groups#theorem-all-left-identities-are-right-identities}{\text{All Left Identities Are Right Identities}}\\
&= z &&\text{by }\href{/groups#definition-group-weak-definition}{\text{Definition: Group (Weak Definition)}}\text{.}
\end{align}$$

## Definition: Group (Strong Definition)

A *group* is a set $$X$$ together with an associative binary operation $$\begin{cases} X \times X \longrightarrow X\\ (x,y) \longmapsto x \cdot y \end{cases}$$ such that:

$$\exists! e \in X \colon \forall x \in X \colon e \cdot x = x \cdot e = x,$$

$$\forall x \in X \colon \exists! x^{-1} \in X \colon x^{-1} \cdot x = x \cdot x^{-1} = e.$$

**Remark.** With the above four theorems, it is easy to show that the strong definition is equivalent to the weak definition.
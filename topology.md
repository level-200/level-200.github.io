---
title: Topology*
permalink: /topology
---

# Topology

## Definition: Topological Space

A *topological space* is any set $$X$$ equipped with a set $$\tau$$ of subsets of $$X$$ such that

$$X \in \tau,$$

$$\forall T \subseteq \tau \colon \bigcup T \in \tau,$$

$$\forall U \in \tau, V \in \tau \colon U \cap V \in \tau.$$

**Additional terminology.** $$\tau$$ is called a *topology* on $$X$$, $$X$$ is called the *underlying set* of the toplogical space, all elements of $$\tau$$ are called *open sets* or *open subsets* of $$X$$, and elements of $$X$$ can be called *points*.

**Motivation.** A topology on a set is meant to represent the set of all ways that set's elements could be "lumped together" or categorized, especially in scenarios where the distinction between individual points is not as important as what category (or categories) those points belong to.

Notice that closure of $$\tau$$ under a single intersection is equivalent to closure under finitely many intersections. We restrict ourselves to finitely many intersections despite allowing arbitrarily many unions to avoid the possibility of having singleton open sets where we don't want them.

## Definition: Standard Topology On $$\mathbb{R}^n$$

For all $$n \in \mathbb{Z} > 0$$, the *standard topology* on $$\mathbb{R}^n$$ is defined as

$$\{U \subseteq \mathbb{R}^n \mid \forall x \in U \colon \exists r > 0 \colon B_r(x) \subseteq U\}.$$

**Remark.** This implies no open set in the standard topology may have boundary. This is where the term *open set* comes from.

Unless otherwise noted, we will assume all $$\mathbb{R}^n$$ to be equipped with the standard topology.

## Definition: Continuous 

Let $$f \colon X \longrightarrow Y$$, where $$X$$ is equipped with topology $$\tau$$ and $$Y$$ is equipped with topology $$\sigma$$, $$f$$ is called *continuous* iff

$$\forall V \in \sigma \colon \{x \in X \mid f(x) \in V\} \in \tau.$$

**Remark.** For all $$m,n \in \mathbb{Z} > 0$$ and all maps $$f \colon \mathbb{R}^m \longrightarrow \mathbb{R}^n$$, where both sets are equipped with the standard topology, this is equivalent to

$$\forall f(x) \in \mathbb{R}^n \colon \exists r > 0, s > 0 \colon B_r(x) \subseteq B_s(f(x)),$$

where, of course,

$$B_r(x) \subseteq X$$

$$B_s(f(x)) \subseteq Y$$

This is where the term *continuous* comes from.

## Definition: Homeomorphism

A *homeomorphism* is a continuous bijection between topological spaces with continuous inverse. 

**Remark.** This means two homeomorphic topological spaces are isomorphic to each other.

## Definition: Subspace Topology

For any set $$X$$ with topology $$\tau$$, the *subspace topology* induced by $$\tau$$ on any $$U \subset X$$ is defined as

$$\{U \cap O \mid O \in \tau\}.$$

**Remark.** Unless otherwise noted, we will assume all subsets of a topological space to be equipped with the subspace topology.

## Definition: Chart

For any topological space $$X$$ with topology $$\tau$$, a *chart* on $$X$$ is a pair $$(U,\varphi)$$ such that $$U \in \tau \neq \varnothing$$ and $$\varphi$$ is a homeomorphism from $$U$$ to some open subset of $$\mathbb{R}^n$$ for some $$n \in \mathbb{Z} > 0$$.

## Definition: Atlas

An *atlas* on any topological space $$X$$ with topology $$\tau$$ is any set of charts on $$X$$ $$\{(U_i, \varphi_i)\}$$ such that

$$\bigcup_i U_i = X.$$

Using $$^{-1}$$ to denote inverse functions, for some $$k \in \mathbb{Z} > 0$$, a $$C^k$$ atlas is one such that for all $$i$$, $$j$$, the function $$\varphi_i \circ \varphi_j^{-1}$$ is $$k$$ times differentiable. A $$C^k$$ atlas is called *maximal* if there exists no chart which can be added to the atlas while preserving its $$C^k$$ structure. *Smooth* ($$C^\infty$$) and *differentiable* atlases and maximal atlases are defined similarly.

**Motivation.** A $$C^k$$ atlas is defined this way so that if, for some $$n \in \mathbb{Z} > 0$$, $$i$$,  $$f \colon X \longrightarrow \mathbb{R}^n$$, $$f \circ \varphi_i^{-1}$$ is $$k$$ times differentiable, then for any $$j$$, $$f \circ \varphi_j^{-1}$$ is also differentiable by the chain rule since

$$f \circ \varphi_j^{-1} = (f \circ \varphi_i^{-1}) \circ (\varphi_i \circ \varphi_j^{-1}),$$

and if instead $$f \colon \mathbb{R}^n \longrightarrow X$$ and $$\varphi_i \circ f$$ is $$k$$ times differentiable, then for any $$j$$, $$\varphi_j \circ f$$ is also differentiable by the chain rule since

$$\varphi_j \circ f = (\varphi_j \circ \varphi_i^{-1}) \circ (\varphi_i \circ f).$$

## Definition: Manifold

A *manifold* is a topological space equipped with an atlas. A *differentiable*, $$C^k$$ (where $$k \in \mathbb{Z} > 0$$), or *smooth* ($$C^\infty$$) manifold is a topological space equipped with a differentiable, $$C^k$$, or smooth atlas, respectively, where the atlas is also maximal. An *$$n$$-dimensional* manifold is one for which all charts have homeomorphisms to open subsets of $$\mathbb{R}^n$$ for the same $$n \in \mathbb{Z} > 0$$.

**Motivation.** A manifold is meant to represent any set which can, at least locally, be visualized as "living in" a Euclidean space. We require maximal atlases so as to avoid imposing unnecessary structure.

## Definition: Differentiable Et Cetera

Where $$M$$ is a $$C^k$$ manifold for some $$k \in \mathbb{Z} > 0$$, $$f \colon M \longrightarrow \mathbb{R}^m$$ for some $$m \in \mathbb{Z} > 0$$, $$g \colon S \subseteq \mathbb{R}^n \longrightarrow M$$ for some $$n \in \mathbb{Z} > 0$$, and $$h \colon M \longrightarrow N$$ for some $$C^k$$ manifold $$N$$:

$$f$$ is called $$C^k$$ iff for all $$x \in M$$ there exists some chart $$(U,\varphi)$$ on $$M$$ such that $$x \in U$$ and $$f \circ \varphi^{-1}$$ is $$k$$ times differentiable, where $$^{-1}$$ denotes an inverse.

$$g$$ is called $$C^k$$ iff for all $$x \in S$$ there exists some chart $$(U,\varphi)$$ on $$M$$ such that $$g(x) \in U$$ and $$\varphi \circ g$$ is $$k$$ times differentiable.

$$h$$ is called $$C^k$$ iff for all $$x \in M$$ there exists some chart $$(U,\varphi)$$ on $$M$$ and some chart $$(V,\phi)$$ on $$N$$ such that $$x \in U$$, $$h(x) \in V$$, and $$\phi \circ h \circ \varphi^{-1}$$ is $$k$$ times differentiable, where $$^{-1}$$ denotes an inverse.

You can guess what it means for $$f$$, $$g$$, or $$h$$ to be *differentiable* or *smooth* ($$C^\infty$$).

**Remark.** The definitions above can be nicely intuitively summarized: A map either between manifolds or between reals and a manifold is $$C^k$$, etc. iff its natural reals-to-reals "counterpart" given by the manifold structure(s) is $$C^k$$, etc.
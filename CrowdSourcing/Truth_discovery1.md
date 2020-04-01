# Truth discovery of correlated entities

## Problem

In the crowdSourcing Problem, the entities may be correlated. Correlation between entities: $S(i,i')$

> hint: extend the objective function

## Optimization

$$
\left.\min _{x^{(i)}, w} f\left(X^{(*)}, W\right)=\sum_{i=1}^{N}\left\{\sum_{k=1}^{K} w_{k}\left\|x_{i}^{(*)}-x_{i}^{(k)}\right\|^{2}+\alpha \sum_{i^{\prime} \in N(i)} S\left(i, i^{\prime}\right)\left\|x_{i^{\prime}}^{(*)}-x_{i}^{(*)}\right\|\right\}^{2}\right\}\\
\text { s.t. } \sum_{k=1}^{K} \exp \left(-w_{k}\right)=1
$$



## Algorithm(paper)

### Attemped Solution and its problem
$$
w_{k}=-\log \left(\frac{\sum_{i=1}^{N}\left\|x_{i}^{(*)}-x_{i}^{(k)}\right\|^{2}}{\sum_{i=1}^{N} \sum_{k^{\prime}=1}^{K}\left\|x_{i}^{(*)}-x_{i}^{\left(k^{\prime}\right)}\right\|^{2}}\right)
$$

$$
x_{i}^{(*)}=\frac{\sum_{k=1}^{k} w_{k} x_{i}^{(k)}+\left(\alpha \sum_{i^{\prime} \in N(i)} S\left(i, 1^{\prime}\right) x_{i'}^{(*)}\right)}{\left.\sum_{k=1}^{K} w_{k}+\alpha \sum_{i^{\prime} \in N(0)} S\left(i, i^{\prime}\right)\right]}
$$
Note that $x_{i}^*$  dependes on $x_{i'}^{*}$ So cannot update like this.

### Proposed solution

Of the relation graph $S(i,i')$. Using **Graph Coloring problem** to find colors so that the variable $x$ can be updated one color after another.


## Discussion

How to model the negative correlation between entities?

> **ycy** In this formulation, the negative correlation can be hardly modeled? \
>if S(i,i')<0 then it is not convex?\
> Can we use a form like gaussian $x^{T} \Sigma x$ to model the negative correlation?

Is that a very simple QP(least squares) in solving $x_{i}^{(*)}$? Why graph colors?
> **ycy** 

## Reference

C. Meng, W. Jiang, Y. Li, J. Gao, Lu Su, H. Ding, Y. Cheng, “Truth Discovery on Crowd Sensing of Correlated Entities”, in SenSys 2015. 
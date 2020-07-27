---
layout: post
title:  "Systemmatic Approach of Time-dependent Perturbation Theory"
date:   2020-07-26
banner_image:
tags: [Quantum Mechanics]
---

In this blog, I will discuss a systemmatic way to perform time-dependent perturbation in Quantum Mechanics. Consider a quantum system evolves under the following Hamiltonian,

$$ H=H_0+H_1(t) $$

where 
$$H_0$$ 
is a time-independent Hamiltonian with known eigenbasis, and 
$$H_1(t)$$ 
is a small time-dependent perturbation. A convenient way to set up the time-dependent perturbation is to use interaction picture, whose states and operators can be transformed from Schrodinger picture as follow. 

$$ A_I(t)=\mathrm{e}^{iH_0t}A_S(t)\mathrm{e}^{-iH_0t} $$

$$ |\psi_I(t)\rangle=\mathrm{e}^{iH_0t}|\psi_S(t)\rangle $$

and the states in interaction picture evolves under the following equation.

$$ i\hbar\frac{\partial}{\partial t}|\psi_I(t)\rangle=H_1^{I}(t)|\psi_I(t)\rangle $$

<!--more-->

So we can define the time evolution operator in interaction picture, where 
$$\mathcal{T}$$ 
is the time-ordering operator.

$$ \begin{aligned}
    U_{I}(t,t_0)&=\mathcal{T}\exp\bigg(-\frac{i}{\hbar}\int_{t_0}^t H_1^{I}(t')\mathrm{d}t'\bigg)\\
    &=1-\frac{i}{\hbar}\int_{t_0}^t H_1^{I}(t')\mathrm{d}t'+\bigg(-\frac{i}{\hbar}\bigg)^2\int_{t_0}^t\mathrm{d}t'\int_{t_0}^{t'}\mathrm{d}t'' H_1^{I}(t')H_1^{I}(t'')+\cdots
\end{aligned} $$

This formula is called Dyson series, which plays a important role in calculation of Feynman diagrams. However, in our case it's more convenient to get rid of the time-ordering operator using an effective Hamiltonian in interaction picture as follows.

$$
U_{I}(T,0)=\exp\bigg(-\frac{i}{\hbar}H_{eff}^{I}T\bigg)
$$

where

$$ 
H_{eff}^{I}=\frac{1}{T}\int_{0}^T H_1^{I}(t')\mathrm{d}t'-\frac{i}{\hbar}\frac{1}{2T}\int_{0}^T\mathrm{d}t_1\int_{0}^{t_1}\mathrm{d}t_2 [H_1^{I}(t_1), H_1^{I}(t_2)]+\cdots
$$

This expression is an immediate consequence of the Magnus expansion. Here we provide a simple proof up to the second order of 
$$H_1^I$$
. Due to the Zassenhaus formula,

$$
\mathrm{e}^{X+Y}=\mathrm{e}^{X}\mathrm{e}^{Y}\mathrm{e}^{-[X,Y]/2}\cdots
$$

we get

$$
\begin{aligned}
U_{I}(T,0)&\approx \exp\bigg[-\frac{i}{\hbar}\int_{0}^T H_1^{I}(t')\mathrm{d}t'\bigg]\exp\bigg[\frac{1}{2}\bigg(-\frac{i}{\hbar}\bigg)^2\int_{0}^T\mathrm{d}t_1\int_{0}^{t_1}\mathrm{d}t_2 [H_1^{I}(t_1), H_1^{I}(t_2)]\bigg]\\
&\approx 1-\frac{i}{\hbar}\int_{0}^T H_1^{I}(t')\mathrm{d}t'+\frac{1}{2}\bigg(-\frac{i}{\hbar}\bigg)^2\int_{0}^T\mathrm{d}t_1\int_{0}^{T}\mathrm{d}t_2 H_1^{I}(t_1)H_1^{I}(t_2)\\
&+\frac{1}{2}\bigg(-\frac{i}{\hbar}\bigg)^2\int_{0}^T\mathrm{d}t_1\int_{0}^{t_1}\mathrm{d}t_2 [H_1^{I}(t_1), H_1^{I}(t_2)]\\
&=1-\frac{i}{\hbar}\int_{0}^T H_1^{I}(t')\mathrm{d}t'+\bigg(-\frac{i}{\hbar}\bigg)^2\int_{0}^T\mathrm{d}t_1\int_{0}^{t_1}\mathrm{d}t_2 H_1^{I}(t_1)H_1^{I}(t_2)\\
\end{aligned}
$$

And we can interpret this idea as the well-known rotating wave approximation (RWA), where the high frequency component is removed by the time average procedure. For example, if we assume

$$
H^I_1(t)=\sum_m (h_m\mathrm{e}^{-i\omega_m t}+h_m^{\dagger}\mathrm{e}^{i\omega_m t})
$$

and we confine our interest to the dynamics occur in the time scale much longer than the period of any possible oscillations, we get

$$
\begin{aligned}
H_{eff}^{I}&\approx -\frac{i}{\hbar}\frac{1}{2T}\int_{0}^T\mathrm{d}t\sum_{mn}\bigg[h_m\mathrm{e}^{-i\omega_m t}+h_m^{\dagger}\mathrm{e}^{i\omega_m t},h_n\frac{\mathrm{e}^{-i\omega_n t}-1}{-i\omega_n}+h_n^{\dagger}\frac{\mathrm{e}^{i\omega_n t}-1}{i\omega_n}\bigg]\\
&\approx \sum_m\frac{1}{\hbar\omega_m}[h_m^{\dagger},h_m]\\
\end{aligned}
$$

---

1. S. Blanes, F. Casas, J. A. Oteo, and J. Ros, *The Magnus expansion and some of its
applications*, arXiv:0810.5488 (2008).

2. Daniel F. V. James, Jonathan Jerke, *Effective Hamiltonian Theory and Its Applications in Quantum Information*, arXiv:0706.1090 (2007).
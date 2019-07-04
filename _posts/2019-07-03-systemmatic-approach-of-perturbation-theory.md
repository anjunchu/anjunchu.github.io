---
layout: post
title:  "Systemmatic Approach of Perturbation Theory"
date:   2019-07-03
banner_image:
tags: [Quantum Mechanics]
---

In this blog, I will discuss a systemmatic way to perform perturbation in Quantum Mechanics.

## Time-independent Perturbation Theory
Consider a quantum system evolves under the following time-independent Hamiltonian,

$$ H=H_0+V $$

where 
$$H_0$$ 
is a Hamiltonian with known eigenbasis 
$$\{|m\rangle\}$$ 
with eigenenergies 
$$\{E^{(0)}_m\}$$
, and 
$$V$$ 
is a small perturbation. A convenient way to perturbatively diagonalize the Hamiltonian is the Schrieffer–Wolff transformation, which is the following unitary transformation with well-chosen generator 
$$S$$
.

$$ H_{\mathrm{eff}}=\mathrm{e}^{-S}He^{S}=H-[S,H]+\frac{1}{2!}[S,[S,H]]+\cdots $$

$$ |\psi_{\mathrm{eff}}\rangle=\mathrm{e}^{-S}|\psi\rangle $$

<!--more-->

This perturbative expansion is valid because 
$$S$$ 
is chosen with the same order as 
$$V$$
. As unitary transformation requires 
$$(\mathrm{e}^{S})^{\dagger}=\mathrm{e}^{-S}$$
, we find 
$$S$$ 
is anti-Hermitian with 
$$S^{\dagger}=-S$$
. In eigenbasis 
$$\{|m\rangle\}$$
, we have 
$$S^{*}_{mn}=-S_{nm}$$
. Suppose we interested in the subspace spanned by some eigenstates with similar energy, whose projection operator is 
$$P_A$$
. And we also define the projection operator out of this subspace as 
$$P_B=1-P_A$$
. Now we can write the Hamiltonian in diagonal part (
$$H_0, H_1$$
) and off-diagonal part (
$$H_2$$
).

$$ H=H_0+H_1+H_2 $$

$$ H_1=P_AVP_A+P_BVP_B $$

$$ H_2=P_AVP_B+P_BVP_A $$

We can also write 
$$S$$ 
as a perturbative series 
$$S=S^{(1)}+S^{(2)}+\cdots$$
, because the leading order of 
$$S$$ 
is the same as 
$$V$$. 

$$ H_{\mathrm{eff}}^{(0)}=H_0 $$

$$ H_{\mathrm{eff}}^{(1)}=H_1+H_2-[S^{(1)},H_0] $$

$$ H_{\mathrm{eff}}^{(2)}=-[S^{(2)},H_0]-[S^{(1)},H_1]-[S^{(1)},H_2]+\frac{1}{2}[S^{(1)},[S^{(1)},H_0]] $$

$$ \cdots $$

As we are interested in the effective Hamiltonian in 
$$P_A$$
, the generator 
$$S$$ 
should be chosen to make the off-diagonal part of each order vanish. For the first order, we have

$$ H_2=[S^{(1)},H_0] $$

If we use 
$$m$$ 
to denote the eigenstates in 
$$P_A$$
, 
$$l$$ 
to denote the eigenstates in 
$$P_B$$
, we have

$$ S^{(1)}_{ml}=\frac{V_{ml}}{E^{(0)}_l-E^{(0)}_m}, \quad S^{(1)}_{lm}=\frac{V_{lm}}{E^{(0)}_m-E^{(0)}_l} $$

where 
$$V_{ml}$$ 
is a shorthand notation for 
$$\langle m|V|l\rangle$$
. As 
$$S^{(1)}$$ 
is off-diagonal, we know that 
$$S^{(1)}H_1$$ 
is off-diagonal, 
$$S^{(1)}H_2$$ is diagonal, so in the second order we have

$$ -[S^{(2)},H_0]-[S^{(1)},H_1]=0 $$

Up to second order perturbation, the effective Hamiltonian in 
$$P_A$$ 
is given by

$$ [H_{\mathrm{eff}}^{(0)}]_{mm'}=[H_0]_{mm'}=E^{(0)}_m\delta_{mm'} $$

$$ [H_{\mathrm{eff}}^{(1)}]_{mm'}=V_{mm'} $$

$$ [H_{\mathrm{eff}}^{(2)}]_{mm'}=-\frac{1}{2}\langle m|[S^{(1)},H_2]|m'\rangle=\frac{1}{2}\sum_{l}V_{ml}V_{lm'}\bigg[\frac{1}{E^{(0)}_m-E^{(0)}_l}+\frac{1}{E^{(0)}_{m'}-E^{(0)}_l}\bigg] $$

Diagonalizing the effective Hamiltonian 
$$H_{\mathrm{eff}}$$ 
up to some order, we can get the eigenenergies 
$$E$$ 
and the eigenstates 
$$|\psi_{\mathrm{eff}}\rangle$$ 
as perturbative expansion. As the unitary transformation cannot change the energy spectrum, 
$$E$$ 
is the eigenenergy of the original Hamiltonian 
$$H$$
. The original eigenstate 
$$|\psi\rangle$$ 
is given by

$$ |\psi\rangle=\mathrm{e}^{S}|\psi_{\mathrm{eff}}\rangle=[1+S^{(1)}+\cdots]|\psi_{\mathrm{eff}}\rangle $$

A special case is the non-degenerate perturbation, where we focus on only one eigenstate 
$$|n\rangle$$
. We can get

$$ E^{(1)}=V_{nn}, \quad E^{(2)}=\sum_{l}\frac{V_{nl}V_{ln}}{E^{(0)}_n-E^{(0)}_l} $$

$$ |n^{(1)}\rangle=S^{(1)}|n^{(0)}\rangle=\sum_l\frac{V_{ln}}{E^{(0)}_n-E^{(0)}_l}|l\rangle $$

## Time-dependent Perturbation Theory
Consider a quantum system evolves under the following Hamiltonian,

$$ H=H_0+H_1(t) $$

where 
$$H_0$$ 
is a Hamiltonian with known eigenbasis 
$$\{|m\rangle\}$$ 
with eigenenergies 
$$\{E^{(0)}_m\}$$
, and 
$$H_1(t)$$ 
is a small time-dependent perturbation which is turned on at 
$$t=0$$
. A convenient way to set up the time-dependent perturbation is to use interaction picture, whose states and operators can be transformed from Schrodinger picture as follow. 

$$ A_I(t)=\mathrm{e}^{iH_0t}A_S(t)\mathrm{e}^{-iH_0t} $$

$$ |\psi_I(t)\rangle=\mathrm{e}^{iH_0t}|\psi_S(t)\rangle $$

and the states in interaction picture evolves under the following equation.

$$ i\hbar\frac{\partial}{\partial t}|\psi_I(t)\rangle=H_1^{I}(t)|\psi_I(t)\rangle $$

So we can define the time evolution operator in interaction picture, where 
$$T$$ 
is the time ordering operator.

$$ \begin{aligned}
    U_{I}(t,t_0)&=T\exp\bigg(-\frac{i}{\hbar}\int_{t_0}^t H_1^{I}(t')\mathrm{d}t'\bigg)\\
    &=1-\frac{i}{\hbar}\int_{t_0}^t H_1^{I}(t')\mathrm{d}t'+\bigg(-\frac{i}{\hbar}\bigg)^2\int_{t_0}^t\mathrm{d}t'\int_{t_0}^{t'}\mathrm{d}t'' H_1^{I}(t')H_1^{I}(t'')+\cdots
\end{aligned} $$

Consider the time-independent eigenstates of 
$$H_0$$ 
denoted by 
$$|i\rangle$$ 
and 
$$|f\rangle$$, the transition amplitude from 
$$|i\rangle$$ 
to 
$$|f\rangle$$ 
is given by

$$ d_{i\rightarrow f}(t)=\langle f|U_{I}(t,0)|i\rangle $$

whose perturbative expansion is as follow. This expansion is valid as long as 
$$|d_{i\rightarrow f}(t)|\ll 1$$ 
when 
$$f\neq i$$
.

$$ d_{i\rightarrow f}^{(0)}(t)=\delta_{fi} $$

$$ d_{i\rightarrow f}^{(1)}(t)=-\frac{i}{\hbar}\int_{t_0}^t \langle f|H_1^{I}(t')|i\rangle\mathrm{d}t'=-\frac{i}{\hbar}\int_{0}^t \mathrm{e}^{i\omega_{fi}t'}\langle f|H_1(t')|i\rangle\mathrm{d}t' $$

$$ \begin{aligned}
    d_{i\rightarrow f}^{(2)}(t)&=\bigg(-\frac{i}{\hbar}\bigg)^2\int_{0}^t\mathrm{d}t'\int_{0}^{t'}\mathrm{d}t'' \langle f|H_1^{I}(t')H_1^{I}(t'')|i\rangle\\
    &=-\frac{1}{\hbar^2}\sum_m\int_{0}^t\mathrm{d}t'\int_{0}^{t'}\mathrm{d}t'' \mathrm{e}^{i\omega_{fm}t'}\mathrm{e}^{i\omega_{mi}t''}\langle f|H_1(t')|m\rangle\langle m|H_1(t'')|i\rangle
\end{aligned} $$

where 
$$\omega_{fi}=(E^{(0)}_f-E^{(0)}_i)/\hbar$$
.

A special case is the periodic perturbation as follow.

$$ H_1(t)=A\mathrm{e}^{-i\omega t}+A^{\dagger}\mathrm{e}^{i\omega t} $$

So we have

$$ \begin{aligned}
    d_{i\rightarrow f}^{(1)}(t)&=-\frac{i}{\hbar}\int_{0}^t\mathrm{d}t' \bigg[\mathrm{e}^{i(\omega_{fi}-\omega)t'}\langle f|A|i\rangle+\mathrm{e}^{i(\omega_{fi}+\omega)t'}\langle f|A^{\dagger}|i\rangle\bigg]\\
    &=-\frac{1}{\hbar}\bigg[\frac{\mathrm{e}^{i(\omega_{fi}-\omega)t}-1}{\omega_{fi}-\omega}\langle f|A|i\rangle+\frac{\mathrm{e}^{i(\omega_{fi}+\omega)t}-1}{\omega_{fi}+\omega}\langle f|A^{\dagger}|i\rangle\bigg]\\
    &\approx -\frac{1}{\hbar}\frac{\mathrm{e}^{i(\omega_{fi}-\omega)t}-1}{\omega_{fi}-\omega}\langle f|A|i\rangle\\
\end{aligned} $$

if we assume 
$$\omega_{fi}\approx \omega$$
. Thus the transition probability is given by

$$ P_{i\rightarrow f}(t)\approx|d_{i\rightarrow f}^{(1)}(t)|^2\approx\frac{|\langle f|A|i\rangle|^2}{\hbar^2}\frac{\sin^2[(\omega-\omega_{fi})t/2]}{[(\omega-\omega_{fi})/2]^2} $$

and the transition rate is

$$ R_{i\rightarrow f}(t)=\frac{\mathrm{d}P_{i\rightarrow f}(t)}{\mathrm{d}t}\approx\frac{2|\langle f|A|i\rangle|^2}{\hbar^2}\frac{\sin[(\omega-\omega_{fi})t]}{\omega-\omega_{fi}} $$

Using

$$ \lim_{t\rightarrow+\infty}\frac{\sin(xt)}{\pi x}=\delta(x) $$

we have

$$ \begin{aligned}
    R_{i\rightarrow f}&=\lim_{t\rightarrow+\infty}R_{i\rightarrow f}(t)=\frac{2\pi}{\hbar^2}|\langle f|A|i\rangle|^2\delta(\omega-\omega_{fi})\\
    &=\frac{2\pi}{\hbar}|\langle f|A|i\rangle|^2\delta(E^{(0)}_f-E^{(0)}_i-\hbar\omega)\\
\end{aligned} $$

This formula is the Fermi golden rule.

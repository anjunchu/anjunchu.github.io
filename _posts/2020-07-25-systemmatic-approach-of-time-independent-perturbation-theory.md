---
layout: post
title:  "Systemmatic Approach of Time-independent Perturbation Theory"
date:   2020-07-25
banner_image:
tags: [Quantum Mechanics]
---

In this blog, I will discuss a systemmatic way to perform time-independent perturbation in Quantum Mechanics. Consider a quantum system evolves under the following time-independent Hamiltonian,

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

---

1. Sergey Bravyi, David P. DiVincenzo, and Daniel Loss, *Schrieffer-Wolff transformation for quantum many-body systems*, arXiv:1105.0675 (2011).

2. Chao-Xing Liu, Xiao-Liang Qi, HaiJun Zhang, Xi Dai, Zhong Fang, and Shou-Cheng Zhang, *Model Hamiltonian for topological insulators*, Phys. Rev. B 82, 045122 (2010).
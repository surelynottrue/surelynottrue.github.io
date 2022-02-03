---
layout: default
title: "#1: Prepping for Topological Insulators"
date: 2022-02-02
latex: True
summary: |
  Understanding Dirac Equations and the motivation behind generating a whole class of materials with a simple higher order correction.
permalink: /posts/topological-insulators
---

## Introduction

People reading this blog probably have heard about topological insulators, and their applications in the world. If you do not have a background, here's how I would explain their importance in the physics of the future.

Wouldn't it be nice to have a system which doesn't care about getting crumpled? How would it be, if we could have a device that can be completely decoupled from the environment? One of the biggest problems that I see in quantum computing hardware today is decoherence. Qubits always will find a way to couple to the external environment. This will introduce noise to the system, which as you would imagine, is not great in any experiment. Now what if we could just eliminate that possibility?

Topology in physics provides an answer to all of these problems in one fell swoop. It is possible (*yes, today!*) to fabricate a system that wouldn't care about smooth changes in material parameters. We could forget about the environment and focus on the matter at hand with these materials. To understand them on a deeper level, we will need some background on Dirac physics. We will use the Dirac equation to show the existence of these materials theoretically first, through some models. We will go through each step carefully and try to understand everything inside out.

## Klein Gordon and Dirac equations

I see the Klein Gordon, and Dirac equations as the relativistic counterparts to the Schrodinger equation. Nobody would go as far to say that the Schrodinger equation doesn't work, but it is important to understand that relativistic corrections might not be needed for all situations. At high velocities of charge carriers though, we expect to see changes. I believe that the high conductance in topological insulators is the reason why we lean towards Dirac descriptions.

This seems like a circular argument to me though. We use the Dirac equation and add constraints to reach a stage where we start seeing some interesting phenomena. It kind of makes sense, because this whole field started at the hands of theoreticians. There doesn't need to be a physical description to start with, and that is what we see. The constraints conveniently place us at a place where we get observables that can be realized in a lab experiment. 

Before getting to TIs, I will go through how we get to the Klein Gordon and Dirac equations. This blog should serve as a stepping stone for people new to the subject, allowing for abstractions to be added later.

### Lorentz covariant and invariant quantities:

A basic physics-english lesson that I learnt: Something is *invariant* if  the thing doesn't change at all. Covariance however allows for some slack. Something is called *covariant* if its form doesn't change over a transformation.

I will refer to quantities as being Lorentz _invariant_ if they do not change at all, and remain constant when I carry on a transformation on them. On the other hand, I will be considering equations Lorentz _covariant_ if they come out of the transformation without any actual change to the equation, or in better words, if their form remains unchanged. Now this won't happen if my equations have varying powers in the four vector components, which I do in the Schrodinger equation:

$$
i \hbar \frac{\partial \psi}{\partial t} = - \frac{\hbar ^2}{2m} \nabla^2\psi \tag{1.1}​​​​​​
$$

This equation will change its form when going from one inertial frame to the other, which I don't have to be happening in our case.

### Klein Gordon from the Correspondence principle:

I have obtained the Schrodinger equation from the non relativistic energy relation given by $E = \boldsymbol{p}^2/2m$​. I had replaced the energy and momentum values here with operators and I could reach equation 1.1. Similarly I would assume that you would reach the relativistic equation if I started with the relativistic energy equation, which is $E=\sqrt{\boldsymbol{p}^2c^2 + m^2c^4}$​​ as I know it. It would be rather hard to Taylor expand this expression though, so I start with the squared equation.

$$
\begin{aligned} E^2 &= \boldsymbol{p}^2c^2 + m^2c^4 \\&=(-\hbar^2c^2\nabla^2 + m^2c^4) \psi = -\hbar^2\frac{\partial^2}{\partial t^2}\psi\end{aligned} \tag{1.2}​​​​​
$$

The connection with the classical and the quantum counterparts that I pulled here is what I call the correspondence principle. Coming back, I see here that I have reached our desired wave equation with same orders on all the components. I can package the whole thing in a clean and compact form:

$$
\left(\partial_\mu\partial^\mu + \left(\frac{mc}{\hbar}\right)^2\right)\psi = 0\tag{1.3}​​​​
$$

The notations here are standard, and I haven't changed anything. I will introduce two new names here, $\hat\Box = \partial_\mu\partial^\mu$​​, is the d'Alembert operator, and $\hbar/mc$​​​​ is the  ​Compton wavelength. Interestingly, this expression is called the _Klein-Gordon_ equation, but it was introduced by Schrodinger, Klein and Gordon. All the three of them.

I see that on solving for the continuity equation, I get the density of the form $\rho = \psi^*\frac{d\psi}{dt} - \text{c.c.}$, which I can very clearly see can go to negatives for a chosen initial value of $\psi$ and $\frac{d\psi}{dt}$. This is an issue, because I do not want our wavefunctions to lead to a negative probability density. This is where I shift to the Dirac equation for a more accurate description in the relativistic regime.

### Dirac equation

Given from what I learnt from the K.G equation, I would have a strict requirement of the density being positive. For that, I would like to have an equation of first order. That in turn, would require me to have the spatial co-ordinates to be in first order too, because of the covariance criterion that I had set earlier. From what I have learnt from multiple sources, I just start with a form that agrees with the condition:

$$
\begin{align}
i\hbar \frac{\partial \psi}{\partial t} &= \left(\frac{\hbar c}{i} \alpha^k \partial_k + \beta mc^2\right)\psi\nonumber\\
i\frac{\partial \psi}{\partial t}&= (\boldsymbol{\alpha}.\boldsymbol{p} + \beta m)\psi
\end{align}
$$

I have set $\hbar=c=1$ when I wrote the second equation. I note that $\alpha ^k$​ and $\beta$​​​ have to be hermitian, in order to keep the whole hamiltonian hermitian. This equation does satisfy the relativistic energy momentum relation, and it has everything in the same order like I wanted. Also, if I am assuming 

$\psi$ to look like $(\psi_1, \psi_2....\psi_n)^T$, then the matrices have to be $(n\times n)$.

Some properties of these $\alpha$​ and $\beta$​ tensors that come into play naturally when I enforce the energy relation. I have listed the direct results here, but one can find them in the book by Franz Gross.

$$
\beta^2 = (\alpha_i)^2 = 1\\ \{\beta, \alpha_i\} = \{\alpha_i, \alpha_j\} = 0\tag{1.5}​
$$

From these relations I can infer a few more things: 

- $\beta$ and $\alpha_i$ are trace-less
- The eigenvalues of the matrices have to be $\pm 1$
- The dimensions of the matrices have to be even
- The number of dimensions must be greater than 2

This paves the way for starting into topological insulators. Pauli matrices (or block forms with Pauli matrices in them) will be what I will be considering for the matrices, as they seem to tick all the boxes for 1.5.

## References

1. Advanced Quantum Mechanics, Franz Schwabl
2. Relativistic Quantum Mechanics and Field Theory, Franz Gross (_pp_ 197-222)

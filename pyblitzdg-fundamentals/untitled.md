---
description: >-
  Learn what inputs you need to provide pyblitzdg with, so that it can provide
  you with useful results
---

# Building blocks of a physical model

## What does a finite element model need?

In mathematical terms, a finite element model creates a discrete representation of a \(continuous\) mathematical model. The mathematical model may be either a single or a set of partial differential equations.

Consider the example of the 2D heat flow equation on the bi-unit square, subject to appropriate initial data and no-flux boundary conditions, i.e.,

$$
\frac{\partial{u}}{{\partial t}} = \kappa \nabla^2 u ,\; \mbox{on}\;\Omega\,, \\ \\
u(x,y, t=0) = u_{init}(x,y) \,,\\
\frac{\partial u}{\partial n} =0 \;\mbox{on}\;\partial{\Omega}\;\mbox{(no flux)}.
$$

{% hint style="info" %}
 The 2D heat flow equation is also called the "diffusion equation", since it also models the transport behaviour of dissolved solutes.
{% endhint %}

In a nutshell, the above lines of mathematical notation tells us that we need to provide as input a physical \(spatial\) domain \(Omega\) with closed boundary \(dOmega\), initial condition data \(u\_{init}\). If you solve this equation \(say, analytically with Fourier series\), you will have the solution u\(x,y,t\) for all times after t=0. That is, the output is a sort of 'animation', if it is visually interpreted as such.

All physical models based on mathematical equations behave in this way, regardless of whether they are steady \(e.g., where the forcing is prescribed, and the ensuing motion is unknown\) or unsteady \(transient heat flow, fluid flow, etc.\) problems.

\[Insert diagram for workflow of solving a PDE\].

In summary, a physical model \(an equation with boundary conditions\) is a sort of "machine", or computing process, that wants as input the initial representation of the field of interest, and the domain under consideration \(e.g., a disk, a cylinder, a box, the surface of an airplane, etc.\). It returns as output, the values of the field of interest for all times in the future.

In order to provide a _discretized_ computer model with initial conditions and a model domain, one needs a _discrete_ representation of both. With Galerkin finite element methods, the first step is to decompose a geometrical representation of a finite domain into manageable pieces or 'elements'. This can be achieved with engineering CAD software, or academic mesh generation software. An example of a cross-platform free open-source software for carrying out such tasks is `Gmsh`.

{% hint style="info" %}
`Gmsh` can be downloaded for your platform at [http://gmsh.info/](http://gmsh.info/).
{% endhint %}



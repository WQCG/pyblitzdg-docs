---
description: >-
  Learn what inputs you need to provide pyblitzdg with, so that it can provide
  you with useful results
---

# Building Blocks of a Physical Model

## What does a finite element model need?

In mathematical terms, a finite element model creates a discrete representation of a \(continuous\) mathematical model. The mathematical model may be either a single or a set of partial differential equations \(PDEs\).

Consider the example of the 2D heat flow equation on the bi-unit square, subject to appropriate initial data and no-flux boundary conditions, i.e.,

$$
\frac{\partial{u}}{{\partial t}} = \kappa \nabla^2 u ,\; \mbox{on}\;\Omega\,, \\ \\
u(x,y, t=0) = u_{init}(x,y) \,,\\
\frac{\partial u}{\partial n} =0 \;\mbox{on}\;\partial{\Omega}\;\mbox{(no flux)}.
$$

{% hint style="info" %}
 The 2D heat flow equation is also called the "diffusion equation", since it also models the transport behaviour of dissolved solutes.
{% endhint %}

In a nutshell, the above lines of mathematical notation tells us that we need to provide as input a physical \(spatial\) domain $$\Omega$$ with closed boundary $$\partial \Omega$$, initial condition data $$u_{init}$$. If you solve this equation \(say, analytically with Fourier series\), you will have the solution $$u(x,y,t)$$ for all times after $$t=0$$. That is, the output is a sort of 'animation', if it is visually interpreted as such.

All physical models based on mathematical equations behave in this way, regardless of whether they are steady \(e.g., where the forcing is prescribed, and the ensuing motion is unknown\) or unsteady \(transient heat flow, fluid flow, etc.\) problems.

![Workflow for obtaining the solution to a physical problem of interest](../.gitbook/assets/method-draw-image-2.svg)

In summary, a physical model \(an equation with boundary conditions\) is a sort of "machine", or computing process, that wants as input the initial representation of the field of interest, and the domain under consideration \(e.g., a disk, a cylinder, a box, the surface of an airplane, etc.\). It returns as output, the values of the field of interest for all times in the future.

### Discretized Spatial Domain

In order to provide a _discretized_ computer model with initial conditions and a model domain, one needs a _discrete_ representation of both. With Galerkin finite element methods, the first step is to decompose a geometrical representation of a finite domain into manageable pieces or 'elements.' This can be achieved with engineering CAD software, or academic mesh generation software. An example of a cross-platform free open-source software for carrying out such tasks is `Gmsh`.

{% hint style="info" %}
`Gmsh` can be downloaded for your platform at [http://gmsh.info/](http://gmsh.info/).
{% endhint %}

We won't get into the details of creating a model geometry and mesh with `Gmsh` just yet. For now, let's consider the second piece of information required by a physical model, the initial condition which depends on the spatially-discretized model domain.

### Discretized Initial Model Data

For heuristic test cases, one often prescribed the initial state in terms of known mathematical functions ,e.g., `exp`, `sin`, `cos`, etc., of the independent spatial variables \(x, y, z\). For more realistic applications, e.g., weather simulation, one most often use a combination of spatial curve-fitting alongside data assimilation techniques which draw in measurement sources to provide initial solution distributions as close to 'truth' as possible. 


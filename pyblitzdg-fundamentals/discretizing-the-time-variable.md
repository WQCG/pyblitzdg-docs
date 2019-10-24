# Discretizing the Time Variable

Unless certain assumptions \(e.g., time-periodicity\) are made regarding the type of PDE solutions are under study, the continuous time variable, t, must be discretized alongside its spatial counterparts \(x,y,z\).

The most commonly used approach for discretizing time in a numerical model is to break the real line into a series of line segments of finite length. A discrete \(usually 'finite difference'\) approximation is applied to the time derivative term, and the solution is evolved forward in time from previous values. This is known as _time-stepping_.

The handling of the other terms in the PDEs causes numerical time discretization methods to branch out into two classes. If the remaining terms are evaluated at the current \(or known\) time \(or extrapolated from known times\), then the time-stepping method is called _explicit_**.** If, instead, the remaining terms are evaluated at the future \(or unknown\) time, then an algebraic equation results and the method is called _implicit_. If a combination if these two techniques is used, the scheme is called implicit-explicit \(IMEX\) or _mixed_.

### Forward Euler Method

Supposing we have a PDE of the form

$$
\frac{\partial u}{\partial t} = \mathbb{L}(u) \,,
$$

where $$\mathbb{L}$$ is a continuous operator acting on $$u$$, the Forward Euler method applies the finite difference approximation to the time-derivative and evaluates the right-hand side at the known time value $$t_n = n \Delta t \,, \mbox{ for } n=0,1,2\cdots$$, i.e.,

$$
\frac{u^{n+1} - u^n}{\Delta t} = \mathbb{L}^n(u^n) \,.
$$

An explicit recipe for the field of interest $$u$$ at the time-level $$n+1$$ can then be found by rearranging as

$$
u^{n+1} = u^{n} + \Delta t \mathbb{L}^n(u^n) \,,
$$

and this expression is known as the Forward Euler Method or simply Euler's Method.

### Backward Euler Method

The backward Euler is the _implicit_ version of Euler's method, since it evaluates the right-hand side operator at the unknown time $$t_{n+1}$$. It may be written as

$$
\frac{u^{n+1} - u^n}{\Delta t} = \mathbb{L}^{n+1}(u^{n+1}) \,.
$$

or



$$
u^{n+1} - \Delta t \mathbb{L}^{n+1}(u^{n+1}) = u^n\,,
$$

and it is clear that explicit formulas are not possible unless the operator $$\mathbb{L}$$ is quite simple. This last form is the prototypical algebraic equation that must be solved for the field $$u^{n+1}$$ in all time-stepping schemes with an implicit part. Although this equation is in general nonlinear, linear approximations are often used in practised, and they can be argued as reasonable approximations provided $$ \Delta t $$ is sufficiently small.


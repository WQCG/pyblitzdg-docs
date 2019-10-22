# Discretizing the Time Variable

Unless certain assumptions \(e.g., time-periodicity\) are made regarding the type of PDE solutions are under study, the continuous time variable, t, must be discretized alongside its spatial counterparts \(x,y,z\).

The most commonly used approach for discretizing time in a numerical model is to break the real line into a series of line segments of finite length. A discrete \(usually 'finite difference'\) approximation is applied to the time derivative term, and the solution is evolved forward in time from previous values. This is known as _time-stepping_.

The handling of the other terms in the PDEs causes numerical time discretization methods to branch out into two classes. If the remaining terms are evaluated at the current \(or known\) time \(or extrapolated from known times\), then the time-stepping method is called _explicit_**.** If, instead, the remaining terms are evaluated at the future \(or unknown\) time, then an algebraic equation results and the method is called _implicit_. If a combination if these two techniques is used, the scheme is called implicit-explicit \(IMEX\) or _mixed_.

...




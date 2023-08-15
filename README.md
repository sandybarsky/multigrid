# multigrid
This program is to solve a nonlinear 2-D pde using a one-step linearization 
 
   It's multigrid, but not full MG. That is, I start at the finest level.
   It's written in C, but a fairly transparent version.
 
  compile with : gcc -O3 non_linear_multigrid.c -lm 
  with gcc version 12
 
   the equation I am solving is :
      (d/dt)u = Nu+f(x,y,t), where N is a slightly non-linear operator.
      N = (\nabla)^2 + function (u)  where \nabla is latex for 
           (d^2/dx^2 + d^2/dy^2)
      (d/dt)u is obviously a single (time) derivative,
      and function(u) is the nonlinear function of u, (no derivatives of u).
      the function f(x,y,t) has mostly been chosen to test the code for a known
      outcome, but can be any 'nice' function.
    The system is 2-dimensional, and has periodic boundary conditions.
 
    N can be any function of u that is continuous on the interval. I have only
    rigorously tested for powers of u, exponentials and some trigonometric 
    The non-linearity is handled by a one-step linearization at the finest
    grid level, and the resulting linear eqn is solved using MG techniques.
    See, for example, the book 'Multigrid' by Trottenberg, Oosterlee, Schuller
    section 5.3.2 and 5.3.3. The exact eqn solved is explained in the
    function mgrid.
    There is also a newton relaxation step performed at the finest level,
    see for example 'Numerical Methods for Differential Equations' by
    Ortega and Poole section 4.4 for a nice introduction.
 
   I've mostly written this as a tutorial code. To that end, I've tried to
   explain what's going on throughout the code. The reader is expected to 
   have a little familiarity with linear MG and finite difference methods.
   And, it's not terribly optimized, as I've tried to keep things transparent
   I'll try to provide some hints for a faster code, but profile it & go from
   there.
 
 

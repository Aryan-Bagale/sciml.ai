@def title = "SciML Numerical Differential Equations Projects – Google Summer of Code"
@def tags = ["home", "sciml", "diffeq"]

# SciML Numerical Differential Equations Projects – Google Summer of Code

## Native Julia ODE, SDE, DAE, DDE, and (S)PDE Solvers

The DifferentialEquations.jl ecosystem has an extensive set of state-of-the-art
methods for solving differential equations hosted by the [SciML Scientific Machine
Learning Software Organization](https://sciml.ai/). By mixing native methods and wrapped
methods under the same dispatch system, [DifferentialEquations.jl serves both as a system to deploy and research the most modern efficient methodologies](https://arxiv.org/abs/1807.06430).
While most of the basic methods have been developed and optimized, many newer
methods need high performance implementations and real-world tests of their
efficiency claims. In this project students will be paired with current
researchers in the discipline to get a handle on some of the latest techniques
and build efficient implementations into the \*DiffEq libraries
(OrdinaryDiffEq.jl, StochasticDiffEq.jl, DelayDiffEq.jl). Possible families of
methods to implement are:

@@tight-list
- Global error estimating ODE solvers
- Implicit-Explicit (IMEX) Methods
- Geometric (exponential) integrators
- Low memory Runge-Kutta methods
- Multistep methods specialized for second order ODEs (satellite simulation)
- Parallel (multithreaded) extrapolation (both explicit and implicit)
- Parallel Implicit Integrating Factor Methods (PDEs and SPDEs)
- Parallel-in-time ODE Methods
- Rosenbrock-W methods
- Approximate matrix factorization
- Runge-Kutta-Chebyshev Methods (high stability RK methods)
- Fully Implicit Runge-Kutta (FIRK) methods
- Anderson Acceleration
- Boundary value problem (BVP) solvers like MIRK and collocation methods
- BDF methods for differential-algebraic equations (DAEs)
- Methods for stiff stochastic differential equations
@@

Many of these methods are the basis of high-efficiency partial differential
equation (PDE) solvers and are thus important to many communities like
computational fluid dynamics, mathematical biology, and quantum mechanics.

This project is good for both software engineers interested in the field of
numerical analysis and those students who are interested in pursuing graduate
research in the field.

**Recommended Skills**: Background knowledge in numerical analysis, numerical
linear algebra, and the ability (or eagerness to learn) to write fast code.

**Expected Results**: Contributions of production-quality solver methods.

**Mentors**: [Chris Rackauckas](https://github.com/ChrisRackauckas), [Kanav Gupta](https://github.com/kanav99) and [Utkarsh](https://github.com/utkarsh530), [Oscar Smith](https://github.com/oscardssmith)

**Expected Project Size**: 175 hour or 350 hour depending on the chosen subtasks.

**Difficulty**: Easy to Hard depending on the chosen subtasks.

## Performance enhancements for differential equation solvers

Wouldn't it be cool to have had a part in the development of widely used efficient differential equation solvers?
DifferentialEquations.jl has a wide range of existing methods and [an extensive benchmark suite](https://github.com/SciML/DiffEqBenchmarks.jl) which is used for tuning the methods for performance.
Many of its methods are already the fastest in their class, but there is still a lot of performance enhancement work that can be done.
In this project you can learn the details about a wide range of methods and dig into the optimization of the algorithm's strategy and the implementation in order to improve benchmarks.
Projects that could potentially improve the performance of the full differential equations ecosystem include:

@@tight-list
- Alternative adaptive stepsize techniques and step optimization
- Pointer swapping tricks
- Quasi-Newton globalization and optimization
- Cache size reductions
- Enhanced within-method multithreading, distributed parallelism, and GPU usage
- Improved automated method choosing
- Adaptive preconditioning on large-scale (PDE) discretizations
@@

**Recommended Skills**: Background knowledge in numerical analysis, numerical
linear algebra, and the ability (or eagerness to learn) to write fast code.

**Expected Results**: Improved benchmarks to share with the community.

**Mentors**: [Chris Rackauckas](https://github.com/ChrisRackauckas) and , [Oscar Smith](https://github.com/oscardssmith)

**Expected Project Size**: 175 hour or 350 hour depending on the chosen subtasks.

**Difficulty**: Easy to Hard depending on the chosen subtasks.

## Discretizations of partial differential equations

There are two ways to approach libraries for partial differential equations (PDEs): one can build "toolkits" which enable users to discretize any PDE but require knowledge
of numerical PDE methods, or one can build "full-stop" PDE solvers for specific
PDEs. There are many different ways solving PDEs could be approached, and here
are some ideas for potential projects:

@@tight-list
1. Automated PDE discretization tooling. We want users to describe a PDE in its mathematical form and automate the rest of the solution process. See [this issue for details](https://github.com/SciML/DifferentialEquations.jl/issues/469).
2. Enhancement of existing tools for discretizing PDEs. The finite differencing (FDM) library [MethodOfLines.jl](https://github.com/SciML/MethodOfLines.jl) could be enhanced to allow non-uniform grids or composition of operators. The finite element method (FEM) library [FEniCS.jl](https://github.com/SciML/FEniCS.jl) could wrap more of the FEniCS library.
3. Full stop solvers of common fluid dynamical equations, such as diffusion-advection-convection equations, or of hyperbolic PDEs such as the Hamilton-Jacobi-Bellman equations would be useful to many users.
4. Using stochastic differential equation (SDE) solvers to efficiently (and highly parallel) approximate certain PDEs.
5. Development of ODE solvers for more efficiently solving specific types of PDE discretizations. See the "Native Julia solvers for ordinary differential equations" project.
@@

**Recommended Skills**: Background knowledge in numerical methods for solving
differential equations. Some basic knowledge of PDEs, but mostly a willingness
to learn and a strong understanding of calculus and linear algebra.

**Expected Results**: A production-quality PDE solver package for some common PDEs.

**Mentors**: [Chris Rackauckas](https://github.com/ChrisRackauckas) and [Alex Jones](https://github.com/xtalax)

**Expected Project Size**: 175 hour or 350 hour depending on the chosen subtasks.

**Difficulty**: Medium to Hard depending on the chosen subtasks.

## Jump Process Simulation Algorithms

Jump processes are a widely used approach for modeling biological, chemical and epidemiological systems that can account for both stochastic interactions, and spatial transport, of proteins/particles/agents. [JumpProcesses.jl](https://github.com/SciML/JumpProcesses.jl/) provides a library of optimized solvers for exactly simulating jump processes, including recently added solvers that allow for the simulation of spatially-distributed jump processes (where particles/agents move on graphs or general meshes). A variety of possible projects to extend and enhance the current tooling include

@@tight-list
- Adding additional stochastic simulation algorithms such as partial propensity methods (either explicitly or via wrapping the C++ [pSSALib](https://github.com/breezerider/pSSAlib)).
- Exploring cache-optimized table and queue data structures to improve performance of current solvers.
- Extending the current graph and spatial algorithms to support interactions between particles/agents at different spatial locations, and developing tooling to automatically calculate transition rates via PDE discretization techniques.
- Extending StochasticDiffEq.jl with τ-leap algorithms to enable the approximate, but more computationally efficient, simulation of jump processes.
- Extending JumpProcesses and StochasticDiffEq with hybrid simulation capabilities, allowing models that mix ODEs, SDE and jump processes and can dynamically partition model components between each mathematical representation as needed to maintain physical accuracy.
- Extending JumpProcesses's simulation algorithm collection to better support time-dependent rate functions and delays.
@@

**Recommended Skills**: An understanding of how the Gillespie method or basic jump process simulation algorithms work, and experience using DiffEqJump.jl to simulate jump processes.

**Expected Results**: Completing one or more of the preceding improvements to the jump process simulation tooling.

**Mentors**: [Samuel Isaacson](https://github.com/isaacsas) and [Chris Rackauckas](https://github.com/ChrisRackauckas).

**Expected Project Size**: 175 hour or 350 hour depending on the chosen subtasks.

**Difficulty**: Medium to Hard depending on the chosen subtasks.

---
layout: project
categories: [projects]
description: A magnetic levitation train simulator based around a custom numerical integrator with a physics model and a control system. The control system was created from scratch for this application. Developed in C++ for my B.Eng.
image: rail.jpg
tags: [programming, C++, BEng]
---

As part of my B.Eng project along with a [Genetic Algorithm Optimization Tool]({% post_url 2013-02-05-genetic-algorithm %}) I designed and implemented a magnetic levitation train simulator. This was based around a numerical model written as a system of non-linear [ODEs](http://en.wikipedia.org/wiki/Ordinary_differential_equation).

The integration algorithm was split into linear and non-linear parts. The linear parts were solved using a [LU-decomposition](http://en.wikipedia.org/wiki/LU_decomposition) to speed up the matrix inversion of the [Backward Euler solver](http://en.wikipedia.org/wiki/Numerical_ordinary_differential_equations). This linear solver was calculated  assuming the non-linear parts were constants. These were then calculated and set to be new constant values. The process was repeated until the non-linear and linear parts agreed on the solution. This was developed from scratch in C++ using a core routine with no memory allocations, optimized carefully for speed.


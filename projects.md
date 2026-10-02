---
layout: page
title: Projects
permalink: /projects.html
---

## CP2K — Performance Optimization of Machine-Learned Potentials

*Fortran/C, OpenMP · MPhil research, University of Cambridge · [merged PR](https://github.com/cp2k/cp2k/pull/5747) · [fork](https://github.com/ClaudioRMalvino/cp2k)*

CP2K is a widely used open-source quantum chemistry and molecular simulation package. For my MPhil research project I profiled its Behler–Parrinello neural-network potential force evaluation with MAQAO and hardware-counter analysis on the CSD3 supercomputer, then optimized it.

- Redesigned the OpenMP parallelization of the neural-network potential forces and merged it into the main CP2K repository: per-thread workspaces with a fixed-order reduction, delivering a 42× speedup over serial on 76 cores (57× over the previous threaded path) with forces bit-identical to serial at any thread count.
- Developed two optimized branches achieving 5.6× single-core and 2.6× full-node (76-core) speedups on a 3,072-atom bulk-water system: replaced an O(N²) pair search with Verlet neighbour/cell lists, added cubic Hermite spline interpolation, and tuned cache, loop, and OpenMP behavior — reproducing upstream energies and forces bit-for-bit.

## Tensile — Linear Algebra Library (in progress)

*C++23 · [source](https://github.com/ClaudioRMalvino/Tensile)*

A header-only linear algebra library I am actively building: expression templates for lazy, single-pass evaluation without temporaries, cache-optimized BLAS-style kernels, LU/Cholesky/QR decompositions, and 64-byte-aligned allocators for SIMD. Tests and benchmarks run under CI.

## Monte Carlo Options Pricer

*C++20, OpenMP, pybind11 · [source](https://github.com/ClaudioRMalvino/Monte-Carlo-Options-Pricer)*

A Monte Carlo engine pricing European call/put options under geometric Brownian motion, exposed to Python via pybind11 with type stubs and a CMake build.

- Parallelized with OpenMP using per-thread RNG streams and deterministic seeding, so prices are exactly reproducible: ~4× speedup on a 4-core/8-thread CPU, with the serial C++ engine ~3.3× faster than pure Python.
- Immutable, const-correct option class with input validation; reproducible benchmark suite; CI on GitHub Actions.

## Parallel Molecular Dynamics Simulation

*C++20, MPI · Cambridge MPhil*

A distributed-memory molecular dynamics simulation (Lennard-Jones, velocity-Verlet) parallelized with MPI across up to 32 cores using particle decomposition and custom MPI struct datatypes. Strong-scaling studies (500–2,000 atoms) quantified speedup and parallel efficiency, with energy conservation verified to under 1% drift.

## Physics-TUI

*Python, Textual · [source](https://github.com/ClaudioRMalvino/Physics-TUI)*

A published interactive terminal app exposing 150 physics equations across 12 domains, with 58 multi-variable solvers and a unit converter. 82 pytest unit tests, strict mypy typing, Black formatting; packaged for pip and uv.

## Physicalc

*Kotlin Multiplatform, Compose · [source](https://github.com/ClaudioRMalvino/Physicalc)*

A cross-platform physics study app for Android and desktop: interactive equation solvers, a 3D vector calculator, and SM-2 spaced-repetition flashcards. Ported from Physics-TUI using AI-assisted translation, with behavior validated against the original implementation.

## Stochastic Ground-State Eigensolver

*Python, Qiskit · Cambridge MPhil*

A Monte Carlo Projected Quantum Eigensolver (MC-PQE) using importance-sampled Hamiltonian terms and walker population control. Reached milli-Hartree (chemical) accuracy on H₃⁺ validated against full configuration interaction, with reblocking-based statistical error analysis, on a modular Qiskit/PySCF pipeline (UCCSD ansatz, Jordan–Wigner mapping).

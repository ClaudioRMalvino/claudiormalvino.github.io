---
layout: page
title: Projects
description: "Performance engineering and scientific computing projects: CP2K OpenMP optimization, a C++23 linear algebra library, a Monte Carlo options pricer, and MPI molecular dynamics."
permalink: /projects.html
---

## CP2K — Performance Optimization of Machine-Learned Potentials
{: #cp2k}

*Fortran/C, OpenMP · MPhil research, University of Cambridge · [merged PR](https://github.com/cp2k/cp2k/pull/5747) · [fork](https://github.com/ClaudioRMalvino/cp2k)*

CP2K is a widely used open-source quantum chemistry and molecular simulation package. For my MPhil research project I profiled its Behler–Parrinello neural-network potential force evaluation with MAQAO and hardware-counter analysis on the CSD3 supercomputer, then optimized it.

### Merged upstream: OpenMP threading over the atom loop

[cp2k/cp2k #5747](https://github.com/cp2k/cp2k/pull/5747), merged 20 August 2026, is now part of the main CP2K repository. I redesigned the OpenMP parallelization of the neural-network potential forces: threads work over atomic centres with per-thread workspaces, and the partial results are summed in a fixed order.

- 42× speedup over serial on 76 cores, and 57× over the previous threaded path, which ran slower with more threads.
- Forces and energies bit-identical to serial at any thread count: the maximum force difference between 1 and 76 threads is exactly zero.

<figure class="figure">
  <a href="{{ '/assets/figures/cp2k-pr-omp-scaling.png' | relative_url }}"><img src="{{ '/assets/figures/cp2k-pr-omp-scaling.png' | relative_url }}" width="2000" height="795" loading="lazy" alt="Two panels for a 1,024-molecule water benchmark from 1 to 76 cores: time per MD step and strong-scaling speedup. The existing OpenMP path stays flat at about 2.5 seconds per step, while the new one falls to 0.05 seconds per step, a 42 times speedup."></a>
  <figcaption>The benchmark figure from the pull request: 1,024 H₂O on one 76-core node. "PR head" is the baseline before my change and "PR head + graft" is with it. Solid lines are OpenMP threads on one MPI rank; dotted lines are pure MPI. The existing OpenMP path does not scale at all; the new one reaches 42× at 76 threads and overtakes pure MPI.</figcaption>
</figure>

### Further optimization in my thesis branches

These branches are in my fork and are not part of upstream CP2K.

- Developed two optimized branches achieving 5.6× single-core and 2.6× full-node (76-core) speedups on a 3,072-atom bulk-water system: replaced an O(N²) pair search with Verlet neighbour/cell lists, added cubic Hermite spline interpolation, and tuned cache, loop, and OpenMP behavior — reproducing upstream energies and forces bit-for-bit.

<figure class="figure">
  <a href="{{ '/assets/figures/cp2k-size-scaling.svg' | relative_url }}"><img src="{{ '/assets/figures/cp2k-size-scaling.svg' | relative_url }}" width="638" height="476" loading="lazy" alt="Four panels of time per MD step against number of atoms for upstream master and the two optimized branches. Master grows roughly quadratically; the optimized branches grow linearly, and their speedup over master rises with system size."></a>
  <figcaption>Size scaling on a full 76-core node. Upstream <code>master</code> grows as O(N²); the optimized branches stay linear, so the speedup rises from about 0.9× at 192 atoms to about 17× at 12,288 atoms.</figcaption>
</figure>

## Tensile — Linear Algebra Library (in progress)

*C++23 · [source](https://github.com/ClaudioRMalvino/Tensile)*

A header-only linear algebra library I am actively building: expression templates for lazy, single-pass evaluation without temporaries, cache-optimized BLAS-style kernels, LU/Cholesky/QR decompositions, and 64-byte-aligned allocators for SIMD. Tests and benchmarks run under CI.

## Monte Carlo Options Pricer

*C++20, OpenMP, pybind11 · [source](https://github.com/ClaudioRMalvino/Monte-Carlo-Options-Pricer)*

A Monte Carlo engine pricing European call/put options under geometric Brownian motion, exposed to Python via pybind11 with type stubs and a CMake build.

- Parallelized with OpenMP using per-thread RNG streams and deterministic seeding, so prices are exactly reproducible: ~4× speedup on a 4-core/8-thread CPU, with the serial C++ engine ~19× faster than pure Python.
- Validated against the Black–Scholes closed form: the pricing error falls as 1/√N across six decades of path count, matching the analytically predicted standard error.
- Immutable, const-correct option class with input validation; reproducible benchmark suite.

<figure class="figure">
  <a href="{{ '/assets/figures/pricer-convergence.svg' | relative_url }}"><img src="{{ '/assets/figures/pricer-convergence.svg' | relative_url }}" width="504" height="324" loading="lazy" alt="Log-log plot of call and put pricing error against number of paths from 100 to 100 million. The measured points lie on the predicted one-over-root-N lines."></a>
  <figcaption>RMS pricing error against the Black–Scholes value over 32 independent seeds. Dashed lines are the predicted standard error, σ/√N; the fitted convergence order is −0.51 for the call and −0.49 for the put.</figcaption>
</figure>

## Parallel Molecular Dynamics Simulation

*C++20, MPI · Cambridge MPhil*

A distributed-memory molecular dynamics simulation (Lennard-Jones, velocity-Verlet) parallelized with MPI across up to 32 cores using particle decomposition and custom MPI struct datatypes. Strong-scaling studies (500–2,000 atoms) quantified speedup and parallel efficiency, with energy conservation verified to under 1% drift. The simulation follows Rahman's 1964 liquid-argon study and reproduces its pair-correlation function. Source is private: assessed coursework.

<figure class="figure">
  <a href="{{ '/assets/figures/md-mpi-speedup.png' | relative_url }}"><img src="{{ '/assets/figures/md-mpi-speedup.png' | relative_url }}" width="2000" height="410" loading="lazy" alt="Four panels of MPI speedup against process count from 1 to 32, for 500, 1,000, 1,500 and 2,000 particles, comparing Euler, velocity-Verlet and RK4 integrators with the ideal linear line."></a>
  <figcaption>Strong scaling from 1 to 32 MPI processes at four system sizes. Speedup tracks the ideal line up to 8 processes, then falls below it as global communication starts to dominate. Select the figure to enlarge.</figcaption>
</figure>

## Physics-TUI

*Python, Textual · [source](https://github.com/ClaudioRMalvino/Physics-TUI)*

A published interactive terminal app exposing 150 physics equations across 12 domains, with 58 multi-variable solvers and a unit converter. 82 pytest unit tests, strict mypy typing, Black formatting; packaged for pip and uv.

## Physicalc

*Kotlin Multiplatform, Compose · [source](https://github.com/ClaudioRMalvino/Physicalc)*

A cross-platform physics study app for Android and desktop: interactive equation solvers, a 3D vector calculator, and SM-2 spaced-repetition flashcards. Ported from Physics-TUI using AI-assisted translation, with behavior validated against the original implementation.

## Stochastic Ground-State Eigensolver

*Python, Qiskit · Cambridge MPhil*

An implementation of the Monte Carlo Projected Quantum Eigensolver (MC-PQE) from [Filip, *J. Chem. Theory Comput.* (2024)](https://doi.org/10.1021/acs.jctc.4c00295), using importance-sampled Hamiltonian terms and walker population control. Recovered the H₃⁺ correlation energy to within 2.3 mE<sub>h</sub> of full configuration interaction, with reblocking-based statistical error analysis, on a modular Qiskit/PySCF pipeline (UCCSD ansatz, Jordan–Wigner mapping). Source is private: assessed coursework.

<figure class="figure">
  <a href="{{ '/assets/figures/eigensolver-dissociation.png' | relative_url }}"><img src="{{ '/assets/figures/eigensolver-dissociation.png' | relative_url }}" width="1600" height="700" loading="lazy" alt="Two panels showing the shift and the projected correlation energy of linear H3+ against bond length from 0.5 to 3.0 ångström, for 10, 100, 1,000 and 10,000 shots. The 10-shot curve deviates; the others overlap."></a>
  <figcaption>Dissociation curve of linear H₃⁺ at four measurement budgets: shift (left) and projected correlation energy (right), with reblocked uncertainty shaded. At 100 shots and above the curves agree; 10 shots is too noisy.</figcaption>
</figure>

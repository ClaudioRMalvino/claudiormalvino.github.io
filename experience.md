---
layout: page
title: Experience
permalink: /experience.html
description: "Education, research and professional experience, and technical skills of Claudio Malvino: MPhil in Scientific Computing (Cambridge), CP2K performance optimization, C++, Fortran, OpenMP and MPI."
---

[Download this as a PDF resume]({{ '/assets/Claudio-Malvino-Resume.pdf' | relative_url }})

## Education

### University of Cambridge

*MPhil in Scientific Computing · Oct 2025 – Sep 2026*

Relevant coursework: High Performance Computing, Numerical Methods, Scientific Computing, GPU Programming.

### CUNY New York City College of Technology

*B.S. Applied Computational Physics, magna cum laude · 2021 – 2023*

GPA: 3.76/4.0.

## Research experience

### MPhil Research Project: Performance Optimization of CP2K

*University of Cambridge · Supervisors: Dr. Christoph Schran, Dr. Peter Cooke · Apr 2026 – Aug 2026*

- Redesigned the OpenMP parallelization of CP2K's neural-network potential forces and merged it into the main CP2K repository ([PR #5747](https://github.com/cp2k/cp2k/pull/5747)): threaded the atomic-centre loop with per-thread workspaces and a fixed-order reduction, delivering a 42× speedup over serial on 76 cores (57× over the previous threaded path) with forces bit-identical to serial at any thread count.
- Profiled the machine-learned interatomic potential (Behler–Parrinello neural network) force evaluation with MAQAO and hardware-counter analysis on the CSD3 supercomputer, isolating the dominant compute bottlenecks.
- Developed two optimized branches of the Fortran/C codebase achieving 5.6× single-core and 2.6× full-node (76-core) speedups on a 3,072-atom bulk-water system by replacing an O(N²) pair search with Verlet neighbour/cell lists, adding cubic Hermite spline interpolation, and tuning cache, loop, and OpenMP behavior, reproducing upstream energies and forces bit-for-bit.

[Benchmarks and figures]({{ '/projects.html#cp2k' | relative_url }})

### REU Fellow

*University of Texas at Dallas · Supervisor: Dr. Michael Kolodrubetz · May 2023 – Jul 2023*

- Built Python simulations of driven 2D hexagonal lattices with tight-binding models to study non-equilibrium (Floquet) topological phases.
- Computed transport properties and identified phase transitions across Floquet, Anderson, and Haldane regimes.

### Undergraduate Researcher

*CUNY New York City College of Technology · Supervisor: Dr. Roman Kezerashvili · Jan 2023 – Sep 2023*

- Derived closed-form solutions to the 2D Schrödinger equation for central and Kratzer-type potentials via the Nikiforov–Uvarov method, contributing to [two peer-reviewed publications]({{ '/publications.html' | relative_url }}).
- Implemented symbolic and numerical computations and 3D probability-density visualizations in Mathematica.

## Professional experience

### Logistics Coordinator

*Reliance Aerospace Assets · Remote, Fort Lauderdale, FL · Jan 2025 – Sep 2025*

- Sourced commercial aircraft parts and brokered their resale, evaluating purchases by comparing acquisition and repair costs against market resale prices.
- Coordinated the repair-and-return cycle with certified repair stations, tracking turnaround times and maintaining full documentation and traceability.
- Managed quotes, invoicing, and shipping logistics across concurrent transactions while working fully remotely and self-directed.

### Physics Tutor

*CUNY New York City College of Technology · New York, NY · Jan 2024 – Dec 2024*

- Tutored undergraduates in introductory and intermediate physics, one-on-one and in small groups, adapting explanations of problem-solving methods to each student's level.

## Technical skills

- **Languages:** C++ (17/20/23), Python, Fortran, Rust, Bash
- **Libraries:** STL, OpenMP, MPI, CUDA, Eigen, Boost, pybind11, NumPy, SciPy, pandas, Qiskit
- **Tools:** CMake, Git, GitHub Actions, GDB, Valgrind, MAQAO, Slurm, Linux, JupyterLab
- **Methods:** Monte Carlo simulation, numerical methods, parallel and distributed computing (MPI/OpenMP), performance profiling and optimization, stochastic processes, AI-assisted development validated through tests and benchmarks

## Honors and awards

NSF REU Fellowship · Daria Boudana Memorial Scholarship · Emerging Scholars Program · Honors Scholars Program

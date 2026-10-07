---
layout: page
title: About
permalink: /about.html
description: "About Claudio Malvino: background in computational physics, an MPhil in Scientific Computing from Cambridge, and an interest in performance engineering and building tools for other people."
---

## Background

I have always been driven by a need to understand fundamental systems, which had initially led me to physics and mathematics. Over time, I found that my true passion lay in the computational machinery used to model those systems such as the algorithms, numerical methods, and low-level software that make scientific discovery possible.

I completed my B.S. in Applied Computational Physics at CUNY New York City College of Technology, where my research on exactly solvable problems in two-dimensional quantum mechanics resulted in [two peer-reviewed publications]({{ '/publications.html' | relative_url }}). Building custom simulation scripts and working with numerical libraries like NumPy, SciPy, Boost, and Eigen showed me the profound impact of well-crafted software. I realized that building the high-performance tools that enable complex research was just as rewarding as the science itself.

To deepen my technical foundation, I earned an MPhil in Scientific Computing from the University of Cambridge. My studies focused on high-performance C++ optimization and atomistic simulations. My thesis specifically accelerating the neural-network potential code within the open-source quantum chemistry and solid-state physics package [CP2K]({{ '/projects.html#cp2k' | relative_url }}).

---

## How I Work

My approach to engineering is guided by empirical measurement, software correctness, and developer experience.

### Data Over Intuition

To my mind, nothing speaks louder than empirical measurement. I rely on profiling, benchmarking, and runtime statistics to drive optimization and project direction. Analyzing cache access patterns, memory management overhead, and hot loops reveals precisely where performance is lost and how system architecture must evolve. Software development, much like physics, is a continuous exercise in testing hypotheses, uncovering edge cases, and refining our understanding against reality.

### Ergonomics Over Raw Power

Performance cannot exist in a vacuum. A tool can be blisteringly fast, but if its API is counter-intuitive, poorly documented, or fragile, it creates friction that destroys productivity. Software ergonomics, safety, and real-world workflows must be held in the exact same regard as execution speed and correctness. I would always prefer to engineer a finely tuned Porsche that delivers reliable performance across real-world conditions than a drag racer that only goes fast in a straight line.

## My Interests

Beyond my core research and professional work, my current technical interests gravitate toward:

**Modern C++ & Metaprogramming**: I really enjoy diving into the weeds of the language's type system and template mechanics. I like digging through the actual C++ Standard Working Draft (eel.is/c++draft), exploring template metaprogramming, and applying those rules to build custom abstractions like custom matrix layouts. I am currently deepening my understanding of the language internals by working my way through Vandevoorde’s C++ Templates: The Complete Guide and Josuttis’s C++ Move Semantics.

**Quantum Infrastructure & Electronic Structure**: Coming from a physics background, I remain highly interested in quantum computing, topological physics, and quantum software engineering. I enjoy exploring advanced electronic structure theory, looking beyond standard Kohn-Sham DFT into models like Møller-Plesset perturbation theory and the Random Phase Approximation.

**Linux Systems & Workflow Ergonomics**: I daily-drive Linux (currently Arch/CachyOS with the hyprland). I care a lot about developer ergonomics, whether that means configuring lightweight, highly customized terminal environments (like Fish shell with Tide) or setting up the perfect CLion and Python (uv) toolchains. I like building environments that get out of the way and let you work fast.

When I’m not writing code or tweaking my Linux configuration, I spend my time exploring history and art, getting outside for a hike, going to museums, or doing a playthrough of Football Manager or Europa Universalis 4.

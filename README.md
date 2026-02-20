# Interactive Physics Particle System

A high-performance, real-time 2D particle engine developed using **C++** and the **raylib** framework. This project simulates complex particle behaviors by integrating Newtonian physics, vector mathematics, and interactive force fields.

---

## Overview

This simulation creates an organic, fluid experience where hundreds of individual particles react to environmental forces and user input. It serves as a foundation for advanced physics-based game mechanics and visual effects.

> **Key Vision:** The project is designed with modularity in mind, aiming to support persistent systems where simulation states or player progress remain consistent across sessions.

---

## Core Features

### Physics Engine
* **Gravitational Acceleration:** Implements a constant downward force ($9.81 \text{ m/s}^2$) affecting every active particle.
* **Linear Drag & Friction:** Particles lose energy over time (multiplied by a friction coefficient of `0.99`) to prevent chaotic velocity buildup and simulate air resistance.
* **Elastic Collisions:** Real-time boundary detection with momentum reversal, causing particles to bounce realistically off the window edges.

### Dynamic Interaction
* **Mouse Attraction:** Particles calculate the distance and direction to the cursor, creating a "swarm" effect as they accelerate toward the user's pointer.
* **Stabilization Mode:** By holding the **[G]** key, the attraction vector is inverted, allowing for particle repulsion and manual flow stabilization.

### Optimization & Lifecycle
* **Erase-Remove Idiom:** Efficient memory management using `std::remove_if` to prune inactive particles from the vector, preventing memory leaks and maintaining 60 FPS.
* **Visual Lifespan:** A 2-second Time-To-Live (TTL) for each particle with dynamic alpha-blending, causing particles to fade out smoothly before being deallocated.

---

## Controls

| Key / Input | Action |
| :--- | :--- |
| **Mouse Movement** | Attracts particles toward the cursor. |
| **Hold [G]** | Reverses force (Repulsion/Stabilization). |
| **Close Window / ESC** | Safely terminates the raylib context. |

---

## Technical Stack & Requirements

* **Language:** C++17 or higher
* **Library:** [raylib](https://www.raylib.com/)
* **Operating Systems:** Windows, Linux, macOS

### Build Instructions

**Windows (MinGW):**
```bash
g++ main.cpp -lraylib -lgdi32 -lwinmm -o particle_sim.exe

# Interactive Particles

> A WebGL experiment and tutorial showcasing how to render and interact with thousands of particles in real-time using Three.js and custom GLSL shaders.

* **Author:** Bruno Imbrizi
* **Repository:** [brunoimbrizi/interactive-particles](https://github.com/brunoimbrizi/interactive-particles)
* **Associated Article:** Published on [Codrops](https://tympanus.net/codrops/)

---

## Overview

The `interactive-particles` project demonstrates a high-performance technique for creating particle systems derived from images. Instead of using CPU-heavy JavaScript calculations for every individual particle, the system offloads position calculations, displacement, and animation to GPU shaders (GLSL), allowing tens of thousands of particles to animate smoothly at 60 FPS.

---

## Technical Concept & Architecture

1. **Particle Distribution:**
   * An image or graphic is sampled to extract pixel coordinates, color data, and alpha values.
   * Particles are mapped directly to corresponding pixel positions in 3D space using `InstancedBufferGeometry` or point cloud geometry.

2. **Off-Screen Interaction Texture:**
   * Cursor and touch movements are drawn onto an off-screen HTML `<canvas>` (often referred to as an interactive texture or hit map).
   * Trails left by cursor movements fade smoothly over time on this canvas.

3. **Shader Displacement:**
   * The off-screen interaction canvas is passed as a texture uniform to custom vertex shaders via GLSL.
   * The vertex shader samples this texture: wherever the cursor has passed, particles receive a displacement offset, creating ripples, scatter effects, or velocity bursts.

---

## Tech Stack & Dependencies

| Tool / Library | Role |
| :--- | :--- |
| **[Three.js](https://threejs.org/)** | Core WebGL 3D rendering library |
| **[GLSLify](https://github.com/glslify/glslify)** | Node-style module system to import/export modular GLSL shader code |
| **[GSAP (GreenSock)](https://greensock.com/)** | Timeline and transition management |
| **[ControlKit](https://github.com/brunoimbrizi/controlkit.js)** | Debug and configuration UI for tweaking parameters in real-time |
| **[Stats.js](https://github.com/mrdoob/stats.js/)** | Frame rate (FPS) and memory performance monitoring |
| **Webpack / Babel** | Asset bundling and modern JavaScript transpilation |

---

## Getting Started

### Prerequisites
* **Node.js** (v12+ recommended)
* **npm** or **yarn**

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/brunoimbrizi/interactive-particles.git
cd interactive-particles
npm install
```

### Development Server

Start the local development server with hot-reloading:

```bash
npm start
```
The demo will typically open at `http://localhost:8080/` or `http://localhost:3000/`.

### Production Build

Bundle and minify assets for deployment:

```bash
npm run build
```
Production files will be output to the `public/` or `dist/` directory.

---

## Key Features

* **High-Density Particle Systems:** Renders tens of thousands of particles with minimal frame drops.
* **GPU-Accelerated Interaction:** Smooth displacement driven by off-screen render targets.
* **Modular Shaders:** Clean shader code separation using GLSLify.
* **Live Tuning:** Built-in parameter adjustments via ControlKit to experiment with particle size, turbulence, and response speed.

---

## License & Usage

* Distributed under standard **Codrops / MIT** terms.
* Free for personal and commercial learning, experiments, and project integrations.
* Direct redistribution or resale as a packaged template/plugin without modification or attribution is prohibited.
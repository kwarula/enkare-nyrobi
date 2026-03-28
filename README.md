<p align="center">
  <img src="https://img.shields.io/badge/WebGPU-Powered-00ffcc?style=for-the-badge&logo=webgl&logoColor=white" alt="WebGPU Powered">
  <img src="https://img.shields.io/badge/Three.js-r183-black?style=for-the-badge&logo=three.js&logoColor=white" alt="Three.js">
  <img src="https://img.shields.io/badge/Vite-6-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite">
</p>

<h1 align="center">Enkare Nyrobi</h1>
<h3 align="center"><em>The Place of Cool Waters</em></h3>

<p align="center">
  An immersive 3D web experience exploring the origins of Nairobi — where ancient cool waters meet the electric pulse of tomorrow.
</p>

<p align="center">
  <a href="https://enkare-nyrobi.vercel.app"><strong>🌊 Experience it live →</strong></a>
</p>

---

## About

**"Enkare Nyrobi"** is the Maasai phrase meaning *"the place of cool waters"* — the origin of Nairobi's name. Before the concrete skyline and bustling matatus, there were cold, clear streams flowing from the highlands where the Maasai found sanctuary.

This project is an interactive 3D experience that pays tribute to that history, blending it with the electric energy of modern Nairobi. Built entirely with **WebGPU** and **Three.js**, it features real-time water simulation, dynamic caustics, and a scroll-driven narrative journey through three chapters:

- **Chapter I: The Place of Cool Waters** — The ancient streams and the Maasai origins
- **Chapter II: The Pulse of the Green City** — Where the wild meets the wired  
- **Chapter III: Electric Dusk** — Nairobi's neon heartbeat at twilight

## Features

- 🌊 **Real-time water simulation** — GPU-accelerated wave physics with interactive mouse ripples
- ✨ **Dynamic caustics** — Light refraction projected onto the pool floor in real-time
- 🏛️ **Procedural architecture** — Arched corridors, columns, and tiled floors generated with code
- 📜 **Scroll-driven narrative** — Camera transitions and blur effects tied to scroll position
- 🔮 **Advanced rendering pipeline** — SSGI (Screen-Space Global Illumination), SSR (Screen-Space Reflections), and TRAA (Temporal Anti-Aliasing)
- 🎛️ **Interactive GUI** — Tweak every visual parameter in real-time (click the ⚙️ icon)
- 📱 **Responsive** — Adapts to any viewport size

## Tech Stack

| Technology | Purpose |
|---|---|
| [Three.js r183](https://threejs.org/) (WebGPU) | 3D rendering engine with TSL (Three Shading Language) |
| [Vite](https://vitejs.dev/) | Build tool and dev server |
| WebGPU Compute Shaders | Water physics simulation (ping-pong height field) |
| GLSL / TSL | Custom materials, caustics, fresnel effects |
| Vanilla CSS | UI styling with CSS custom properties |
| Google Fonts | Space Grotesk + DM Sans typography |

## Getting Started

### Prerequisites

- **Node.js** 18+
- A **WebGPU-compatible browser**:
  - Chrome 113+ ✅
  - Edge 113+ ✅
  - Firefox Nightly (with `dom.webgpu.enabled` flag) ⚠️
  - Safari — not yet supported ❌

### Installation

```bash
# Clone the repository
git clone https://github.com/kwarula/enkare-nyrobi.git
cd enkare-nyrobi

# Install dependencies
npm install

# Start the development server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in a WebGPU-compatible browser.

### Build for Production

```bash
npm run build
```

Output is generated in the `dist/` directory.

## Deployment

This project is configured for **Vercel** out of the box:

- `vercel.json` includes required `Cross-Origin-Opener-Policy` and `Cross-Origin-Embedder-Policy` headers for WebGPU
- `vite.config.js` targets `esnext` for top-level await support
- Framework auto-detected as Vite

Simply connect the repo to [Vercel](https://vercel.com/new) and deploy. No environment variables required.

## Project Structure

```
enkare-nyrobi/
├── index.html          # Main page with HTML content, CSS, and SEO meta tags
├── scene.js            # 3D scene setup, architecture, lighting, camera, and animation loop
├── WaterPlane.js       # GPU compute-based water simulation (ping-pong wave equation)
├── WaterCaustics.js    # Real-time caustic rendering via light refraction projection
├── vite.config.js      # Vite build configuration
├── vercel.json         # Vercel deployment config with security headers
└── package.json        # Dependencies and scripts
```

## How It Works

### Water Simulation
The water surface uses a **GPU compute shader** running a discretized wave equation on a ping-pong height field buffer. Mouse interaction creates ripples by perturbing the height field, and ambient Perlin noise adds organic movement.

### Caustics
Caustic patterns are computed by projecting refracted light rays from the water surface down to the pool floor. The ratio of the original triangle area to the projected triangle area determines light concentration — creating the signature dancing light patterns.

### Rendering Pipeline
The scene uses a multi-pass rendering pipeline:
1. **Scene Pass** with MRT (Multiple Render Targets) outputting color, normals, velocity, and metallic/roughness
2. **SSGI** for ambient occlusion and global illumination bounce
3. **SSR** for reflections on the water surface
4. **TRAA** for temporal anti-aliasing
5. **Gaussian Blur** for depth-of-field effects on scroll

## Credits

- Built on a remix of [Circle of Water](https://threejs.org/examples/#webgpu_water) from the Three.js examples
- Typography: [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) & [DM Sans](https://fonts.google.com/specimen/DM+Sans)
- Inspired by the history and spirit of Nairobi, Kenya 🇰🇪

## License

MIT

---

<p align="center">
  <em>Before the concrete, there was the current.</em>
</p>

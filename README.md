# 🍉 Melon Jelly

An interactive 3D watermelon-jelly slice you can stretch, poke and cut with a knife. It runs in the browser as **one self-contained HTML file** with real soft-body physics and a custom WebGPU renderer. No libraries, no build step.

> **Live demo:** `https://jojin1709.github.io/melon-jelly-webgpu/`
> **Needs WebGPU:** recent Chrome or Edge on desktop, or another browser with WebGPU turned on.

<!-- Add a screenshot or GIF here: ![Melon Jelly](screenshot.png) -->

---

## ✨ Features

- **Soft-body jelly:** a tetrahedral mesh solved with XPBD at a fixed 60 Hz. The rind is about 3× stiffer than the flesh.
- **Hand tool:** grab any part and pull, scroll or use two fingers to twist, and tap a piece to flick it.
- **Knife tool:** draw a line across the slice and the knife lines up and cuts it into pieces. You can cut pieces again, up to 14 pieces.
- **Angled cuts:** rotate the cut angle in 15° steps for one-tap cuts.
- **Undo cut:** step back through your cuts.
- **Jelly look:** refraction, thickness-based absorption, Fresnel reflection, soft shadows and tone mapping. Seeds and air bubbles ride along inside the flesh.
- **Varieties:** Crimson, Golden, Rosé, Lime, Ube and Berry, plus a custom colour picker.
- **Texture presets:** Gelatin, Mochi and Slime, with Firmness and Internal damping sliders.
- **Sound:** squish, wobble, wet slice and undo sounds made with WebAudio, plus optional ambient music and a volume slider.
- **Extras:** Night studio mode, auto-orbit, low gravity, slow-mo cuts, ¼ speed, show mesh, phone haptics, save PNG, record 6 s as WebM, and a share link.
- **Live readouts:** mass, volume, kinetic energy, pieces, and cut counts.
- **Accessibility:** visible focus outlines, labelled controls, bigger touch targets on phones, and reduced-motion support.

---

## 🚀 Run it

No install needed.

```bash
git clone https://github.com/jojin1709/melon-jelly-webgpu.git
cd melon-jelly-webgpu
```

Then open `index.html` in a WebGPU-capable browser. Or serve it locally:

```bash
npx serve .
```

### Deploy

- **GitHub Pages:** Settings → Pages → deploy from the `main` branch, root folder.
- **Vercel / Netlify:** import the repo as a static site, with no build command.

---

## 🎮 Controls

| Key | Action |
|---|---|
| `H` | Hand tool |
| `K` | Knife tool |
| `C` | Cut across the slice (`Shift+C` for the other direction) |
| `[` `]` | Rotate cut angle |
| `Z` | Undo cut |
| `N` | Give it a nudge |
| `R` | Reset |
| `P` | Save PNG |
| `O` | Auto-orbit |
| `D` | Night studio |
| `Space` | Pause |

**Mouse and touch**
- **Hand:** drag to pull, scroll or add a second finger to twist, and tap to flick.
- **Knife:** drag a line across the jelly and release to cut.

---

## 🧪 How it works

- **Physics:** the slice is a volumetric mesh of tetrahedra solved with XPBD. Damping acts only on relative velocity along the mesh edges, so pieces still fall and tumble freely while the wobble settles.
- **Cutting:** every piece is a convex outline in the slice's rest plane. A stroke fixes a vertical blade plane, each piece is clipped against it, and every new piece gets its own simulation and render mesh.
- **Surface:** the smooth surface, seeds and bubbles are separate meshes pinned to tetrahedra with barycentric weights, so they stretch and turn with the jelly.
- **Rendering:** WGSL shaders draw the floor, seeds and bubbles first, then measure how much jelly each view ray crosses and use that for refraction and absorption.

The full write-up is in the "Inside the experiment" panel on the page.

---

## 🌐 Browser support

| Browser | Status |
|---|---|
| Chrome / Edge (desktop, recent) | ✅ WebGPU on by default |
| Chrome on Android (recent) | ✅ on supported devices |
| Safari 26+ | ✅ WebGPU supported |
| Firefox | ⚠️ depends on version and flags |

If WebGPU isn't available, the page shows a fallback card instead of crashing.

---

## ⚠️ Known limits

- Needs WebGPU, and there is no WebGL fallback yet.
- Only the wedge shape for now.
- The Quality toggle lowers render resolution only. Mesh density is not adjustable yet.

## 🗺️ Ideas for later

- New shapes (cube, wedge, whole melon)
- WebGL fallback
- Mesh-density quality setting
- Bite mode, floor ripples, drag-and-stack pieces

---

## 👤 Author

Developed by **[JOJIN JOHN](https://www.linkedin.com/in/jojin-john/)**

- GitHub: [@jojin1709](https://github.com/jojin1709)
- LinkedIn: [jojin-john](https://www.linkedin.com/in/jojin-john/)

## 📄 License

MIT. See `LICENSE`.
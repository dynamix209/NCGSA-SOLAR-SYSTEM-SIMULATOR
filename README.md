# NCGSA Solar System Simulator

Interactive 3D solar system simulator with real Keplerian orbits, NASA-inspired data, moons, belts, and surface/visibility tools.

Built for **NCGSA** (National Centre of GIS & Space Applications) — Pakistan.

## Features

- Real **Keplerian orbits** (J2000 elements) for the eight planets  
- Soft-scaled planet sizes (Sun remains largest)  
- Major **moons** (Galilean, Saturnian, Martian, etc.) with crust-style procedural maps  
- Saturn **rings** (band meshes + circular particle layer)  
- Asteroid belt, Kuiper belt, and compressed Oort cloud  
- Dwarf planets and major asteroids (Ceres, Pluto, …)  
- **Simulated date** + variable simulation speed  
- Visibility windows from **Islamabad** (or browser geolocation)  
- Constellation panel and planet HUD  

## Project structure

```
ncgsa-solar-system/
├── index.html          # Page markup
├── css/
│   └── styles.css      # UI styles
├── js/
│   └── simulator.js    # Three.js scene, orbits, moons, HUD logic
└── README.md
```

## Requirements

- Modern browser with **WebGL** (Chrome, Firefox, Edge, Safari)  
- Internet connection (loads Three.js + optional texture CDNs)

## Run locally

Because some browsers restrict modules/`file://` quirks less with a small server:

```bash
# Python 3
cd ncgsa-solar-system
python3 -m http.server 8080
```

Then open: [http://localhost:8080](http://localhost:8080)

Or open `index.html` directly in the browser (usually works for this project).

## Upload to GitHub

```bash
cd ncgsa-solar-system
git init
git add .
git commit -m "Initial commit: NCGSA Solar System Simulator"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ncgsa-solar-system.git
git push -u origin main
```

### GitHub Pages (optional)

1. Repo → **Settings** → **Pages**  
2. Source: **Deploy from a branch** → `main` / `/ (root)`  
3. Site URL: `https://YOUR_USERNAME.github.io/ncgsa-solar-system/`

## Controls

| Action | How |
|--------|-----|
| Orbit camera | Drag |
| Zoom | Scroll |
| Select planet | Click body or right-side chip |
| Focus moon | Open planet HUD → moon chips, or click moon |
| Play / pause | Dock ▶/❚❚ |
| Speed | Simulation speed slider |
| Reset date | Jump to today |
| Full view | Full system |

## Tech

- [Three.js r128](https://threejs.org/) (CDN)  
- Vanilla HTML / CSS / JavaScript (no build step)  
- Orbital elements: approximate JPL-style J2000 series  
- Textures: Solar System Scope (CC BY 4.0), NASA 3D Resources where available; procedural fallbacks when maps fail CORS/load  

## Credits

- **NCGSA** — project branding  
- NASA / JPL — fact sheets & orbital context  
- Solar System Scope — planetary maps  
- three.js — WebGL engine  

## License

Educational use. Texture assets remain under their original licenses (see Solar System Scope / NASA terms). Code in this repo: use and adapt with attribution to NCGSA where appropriate.


## If you only see a white page with text

That means **CSS and/or JS did not load**. Common causes:

1. **Only `index.html` was uploaded** — you must also upload the `css/` and `js/` folders.
2. **Wrong folder on GitHub Pages** — `index.html` must be at the repo root (or the folder you set as Pages root), with:
   ```
   index.html
   css/styles.css
   js/simulator.js
   ```
3. **Nested folder by mistake** — if you uploaded the zip so paths become `ncgsa-solar-system/ncgsa-solar-system/index.html`, Pages will not find assets.

### Easiest fix (single file)

Use the all-in-one file instead:

1. Rename `index.standalone.html` → `index.html`
2. Upload **only that one file** to the repo root
3. Enable GitHub Pages

Everything (HTML + CSS + JS) is inside that single file.

### Check

Open the browser console (F12). If you see:
- `Failed to load ./css/styles.css` → upload `css/`
- `Failed to load ./js/simulator.js` → upload `js/`
- `THREE is not defined` → CDN blocked; try another network

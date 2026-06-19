# Cyberpunk Design System Specification (PEFL Compliant)

This document outlines the core tokens, graphical design rules, and CSS properties required to replicate the **Neon Cyberpunk Aesthetic** implemented in the Rubens Rainelli Portfolio.

---

## 🎨 Color Palette & Glow Tokens

The theme balances a deep, lightless space background with high-saturation neon emission lines.

| Token | CSS Variable | Hex Code | Purpose |
| :--- | :--- | :--- | :--- |
| **Space Black** | `--bg-color` | `#050508` | Main canvas background |
| **Grid Cyan** | `--bg-grid-color` | `rgba(0, 240, 255, 0.04)` | Micro grid structure lines |
| **Grid Red** | `--bg-grid-line` | `rgba(255, 0, 85, 0.02)` | Major grid alignment markers |
| **Cyber Slate** | `--card-bg` | `rgba(10, 10, 16, 0.7)` | Panel/card containers background |
| **Frame Gray** | `--card-border` | `#1f1f2e` | Default inactive container borders |
| **Neon Cyan** | `--neon-cyan` | `#00f0ff` | Primary interaction, links, scrollbars |
| **Neon Magenta** | `--neon-magenta` | `#ff0055` | Secondary accents, primary headers, glitch overlays |
| **Neon Yellow** | `--neon-yellow` | `#fefe00` | EULA/Alert flags, system selectors |
| **Neon Green** | `--neon-green` | `#39ff14` | Status badges (Active/Online), indicators |
| **Neon Red** | `--neon-red` | `#ff3333` | Warnings, decommissioned status, errors |

### Glow Formulas
To create realistic light-emission (neon glow) effects, combine small-radius solid glows with large-radius semi-transparent glows:

```css
/* Cyan Neon Glow */
--neon-cyan-glow: rgba(0, 240, 255, 0.4);
box-shadow: 0 0 5px var(--neon-cyan), 0 0 15px var(--neon-cyan-glow);
text-shadow: 0 0 5px var(--neon-cyan-glow);

/* Magenta Neon Glow */
--neon-magenta-glow: rgba(255, 0, 85, 0.4);
box-shadow: 0 0 5px var(--neon-magenta), 0 0 15px var(--neon-magenta-glow);
text-shadow: 0 0 5px var(--neon-magenta-glow);
```

---

## 🅰️ Typography Hierarchy

To maintain the digital, military-tactical dashboard contrast, use the following font hierarchy:

1. **Primary Headers / Branding**: `Orbitron` (sans-serif)
   - *Characteristics*: Geometric, wide letterforms, uppercase.
   - *CSS*: `font-family: 'Orbitron', sans-serif; font-weight: 700; letter-spacing: 2px; text-transform: uppercase;`
2. **Technical Metrics / Buttons / Status**: `Share Tech Mono` (monospace)
   - *Characteristics*: Modern monospaced, compact, clean.
   - *CSS*: `font-family: 'Share Tech Mono', monospace; letter-spacing: 1px; text-transform: uppercase;`
3. **Body Descriptions**: `Inter` or `Roboto` (sans-serif)
   - *Characteristics*: Clean, high-legibility sans-serif, neutral.
   - *CSS*: `font-family: 'Inter', sans-serif; font-weight: 300; line-height: 1.6;`

---

## ⚡ CSS Effects & Animations

### 1. The Glitch Text Effect
Simulates database desynchronization. It uses double-layered pseudo-elements (`::before` and `::after`) shifted horizontally with erratic clip-paths.

```css
.title-glitch {
  position: relative;
  text-shadow: -2px -2px 0 var(--neon-cyan), 2px 2px 0 var(--neon-magenta);
}

.title-glitch::before, .title-glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0; left: 0; width: 100%; height: 100%;
  background: var(--bg-color);
  overflow: hidden;
}

.title-glitch::before {
  left: -2px;
  text-shadow: 1px 0 var(--neon-magenta);
  clip: rect(0, 900px, 0, 0);
  animation: noise-anim 2s infinite linear alternate-reverse;
}

.title-glitch::after {
  left: 2px;
  text-shadow: -1px 0 var(--neon-cyan);
  clip: rect(0, 900px, 0, 0);
  animation: noise-anim-2 3s infinite linear alternate-reverse;
}

@keyframes noise-anim {
  0% { clip: rect(2px, 9999px, 80px, 0); }
  20% { clip: rect(60px, 9999px, 12px, 0); }
  40% { clip: rect(15px, 9999px, 50px, 0); }
  60% { clip: rect(75px, 9999px, 85px, 0); }
  80% { clip: rect(4px, 9999px, 20px, 0); }
  100% { clip: rect(90px, 9999px, 45px, 0); }
}

@keyframes noise-anim-2 {
  0% { clip: rect(40px, 9999px, 60px, 0); }
  20% { clip: rect(10px, 9999px, 80px, 0); }
  40% { clip: rect(90px, 9999px, 15px, 0); }
  60% { clip: rect(5px, 9999px, 50px, 0); }
  80% { clip: rect(70px, 9999px, 95px, 0); }
  100% { clip: rect(25px, 9999px, 30px, 0); }
}
```

### 2. CRT Scanline Overlay
Adds a retro-futuristic monitor scanline texture.

```css
body::after {
  content: " ";
  display: block;
  position: fixed;
  top: 0; left: 0; bottom: 0; right: 0;
  background: 
    linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), 
    linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
  z-index: 9999;
  background-size: 100% 4px, 6px 100%;
  pointer-events: none;
  opacity: 0.4;
}
```

---

## 📐 Layout Rules & Shapes

To distinguish cyberpunk containers from normal web blocks, employ non-orthogonal corners using `clip-path`.

### 1. The Cyberpunk Octagon Card
```css
.project-card {
  clip-path: polygon(0 0, 100% 0, 100% 92%, 92% 100%, 0 100%);
}
```

### 2. Angular Buttons
```css
.lang-btn {
  clip-path: polygon(0 0, 85% 0, 100% 100%, 15% 100%);
}
```

### 3. Corner Brackets (Tech Accents)
Place absolute-positioned indicators or borders around dashboards:
```css
.dashboard::before {
  content: "";
  position: absolute;
  top: -1px; left: -1px;
  width: 15px; height: 15px;
  border-top: 2px solid var(--neon-cyan);
  border-left: 2px solid var(--neon-cyan);
}
```

# Cyberpunk Vector Graphics (SVG) Guide

This guide defines the design tokens and structural patterns for creating lightweight, scalable, and responsive **vector illustrations (SVGs)** that align with the neon-cyberpunk UI layout.

---

## 📐 Document Structure & Canvas

All vector assets must be uniform in scaling, viewport coordinates, and background color.

- **viewBox**: Always set the canvas viewport to `0 0 400 250` (or another uniform aspect ratio, e.g. 1.6:1).
- **Background**: Start the document with a solid black-indigo backdrop to block external pages:
  ```xml
  <rect width="100%" height="100%" fill="#0a0a0f"/>
  ```
- **Grid Overlay**: Embed a subtle background grid pattern to simulate technical drawing sheets:
  ```xml
  <path d="M 0,50 L 400,50 M 0,100 L 400,100 M 0,150 L 400,150 M 0,200 L 400,200 M 50,0 L 50,250 M 100,0 L 100,250 M 150,0 L 150,250 M 200,0 L 200,250 M 250,0 L 250,250 M 300,0 L 300,250 M 350,0 L 350,250" stroke="#141424" stroke-width="1"/>
  ```

---

## ⚡ Neon Glow Filter Patterns

SVG filters use Gaussian blur combined with the original graphic to yield a realistic light emission effect. Always define these filters inside a `<defs>` tag at the beginning of the SVG.

### SVG Filter Template
```xml
<defs>
  <!-- Neon Cyan Glow -->
  <filter id="glow-cyan" x="-30%" y="-30%" width="160%" height="160%">
    <feGaussianBlur stdDeviation="5" result="blur" />
    <feMerge>
      <feMergeNode in="blur" />
      <feMergeNode in="SourceGraphic" />
    </feMerge>
  </filter>

  <!-- Neon Magenta Glow -->
  <filter id="glow-magenta" x="-30%" y="-30%" width="160%" height="160%">
    <feGaussianBlur stdDeviation="6" result="blur" />
    <feMerge>
      <feMergeNode in="blur" />
      <feMergeNode in="SourceGraphic" />
    </feMerge>
  </filter>

  <!-- Neon Green Glow -->
  <filter id="glow-green" x="-30%" y="-30%" width="160%" height="160%">
    <feGaussianBlur stdDeviation="5" result="blur" />
    <feMerge>
      <feMergeNode in="blur" />
      <feMergeNode in="SourceGraphic" />
    </feMerge>
  </filter>
</defs>
```

---

## 🛰 Core Visual Elements

To build the cyberpunk schematic look, use these four visual primitives:

### 1. Circuit Traces & Nodes
Draw lines with 45-degree angle bends and terminate them with small circle nodes:
```xml
<!-- Circuit Line -->
<path d="M 50,75 L 120,75 L 150,105 L 150,170" fill="none" stroke="#00f0ff" stroke-width="1.5" opacity="0.5"/>
<!-- Node End -->
<circle cx="50" cy="75" r="3.5" fill="#00f0ff" filter="url(#glow-cyan)"/>
```

### 2. High-Tech Hexagonal Frameworks
Use polygons with coordinate offsets to create futuristic hex capsules:
```xml
<!-- Centered Octagonal Panel Frame -->
<polygon points="-60,-80 60,-80 100,-40 100,40 60,80 -60,80 -100,40 -100,-40" fill="#0d0d18" stroke="#ff0055" stroke-width="2" filter="url(#glow-magenta)"/>
```

### 3. Laser Grid Alignment Lines
Draw dotted line arrays with opacity decays:
```xml
<line x1="20" y1="40" x2="380" y2="40" stroke="#ff0055" stroke-width="1.5" opacity="0.8" stroke-dasharray="10 5"/>
```

### 4. Technical Status Labels
Use monospaced fonts, tiny sizes, capital letters, and bracket wrappers:
```xml
<text x="200" y="220" fill="#39ff14" font-family="'Share Tech Mono', monospace" font-size="9" text-anchor="middle" letter-spacing="2">SYS_AUDIT: OK</text>
```

---

## 🎨 Hex Colors matching UI
When writing SVG XML directly, apply these exact color codes to maintain theme unity:
- **Neon Cyan**: `#00f0ff`
- **Neon Magenta**: `#ff0055`
- **Neon Yellow**: `#fefe00`
- **Neon Green**: `#39ff14`
- **Dark Grid Lines**: `#141424`
- **Grid Embers**: `rgba(255, 0, 85, 0.05)`

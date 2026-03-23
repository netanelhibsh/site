# Netanel Hibsh — Brand Design System

## Colors

### Primary Palette
| Name | Hex | Usage |
|------|-----|-------|
| **Background** | `#0a0a14` | רקע ראשי בכל הדפים |
| **Card** | `#12121e` | רקע כרטיסים, אלמנטים |
| **Gold** | `#e2b21f` | Accent ראשי, highlights, מחירים |
| **Gold Light** | `#f5d060` | Gradient gold (edge) |
| **Magenta** | `#c20078` | CTAs, כפתורים ראשיים, accents |
| **Magenta Light** | `#e84aad` | Gradient magenta (edge) |
| **Teal** | `#5b959e` | Section labels, accents משניים |
| **Teal Light** | `#7eb8c1` | Gradient teal (edge) |

### Text
| Name | Hex | Usage |
|------|-----|-------|
| **Primary** | `#f0f0f5` | כותרות, טקסט ראשי |
| **Muted** | `#8b8ba3` | תיאורים, subtitles |
| **Dim** | `#6b7280` | meta text, footer |

### Borders & Effects
| Name | Value | Usage |
|------|-------|-------|
| **Border** | `rgba(255,255,255,0.08)` | גבולות כרטיסים |
| **Glow Magenta** | `0 0 40px rgba(194,0,120,0.3)` | CTAs ראשיים |
| **Glow Gold** | `0 0 40px rgba(226,178,31,0.3)` | Blueprint accent |
| **Glow Teal** | `0 0 40px rgba(91,149,158,0.3)` | Partnerships accent |

---

## Typography

### Font
**Almoni** (5 weights: 300, 400, 500, 700, 900)

### Scale (MiriKnows DNA)
| Element | Size | Weight | Line-Height | Letter-Spacing |
|---------|------|--------|-------------|----------------|
| **body** | 17px | 400 | 1.7 | — |
| **Hero H1** | clamp(40px, 7vw, 72px) | 900 | 1.1 | -1px |
| **H1 .highlight** | (inherit) | (inherit) | — | — color: var(--gold) |
| **Hero subtitle** | clamp(18px, 3vw, 22px) | 300 | 1.6 | — |
| **Hero badge** | 15px | 500 | — | 0.8px |
| **Section label** | 13px | 700 | — | 2px, uppercase |
| **Section title (H2)** | clamp(28px, 4vw, 40px) | 800 | 1.2 | — |
| **Section desc** | 18px | 300 | 1.6 | — |
| **Card title (H3)** | 20px | 700 | — | — |
| **Card desc** | 15px | 300 | 1.6 | — |
| **Footer** | 14px | 400 | — | — |

---

## Components

### Nav
- Fixed top, padding 16px 0
- Scrolled: `background: rgba(10,10,20,0.95); backdrop-filter: blur(12px); box-shadow: 0 2px 24px rgba(0,0,0,0.4);`
- Logo: height 32px
- **Nav CTA: ALWAYS magenta gradient** (every page)

### Buttons
- **Primary CTA** (hero, final): `background: linear-gradient(135deg, var(--magenta), var(--magenta-light)); color: #fff; padding: 16px 40px; border-radius: 100px; font-size: 18px; font-weight: 700;`
- **Page accent CTA** (hero only): same specs, page accent color gradient
- **Outline CTA**: `border: 1px solid [accent]; background: transparent; color: [accent]; same padding/radius`

### Cards
- `background: #12121e; border: 1px solid rgba(255,255,255,0.08); border-radius: 16px; padding: 32px;`
- Hover: `transform: translateY(-6px); border-color: [accent];`

### Hero
- `min-height: 100vh; display: flex; align-items: center; justify-content: center; text-align: center; padding: 140px 24px 100px;`
- Radial gradient glows in background
- 6 floating nodes (magenta, gold, teal)

### Sections
- Padding: `100px 0`
- Container: `max-width: 1100px; margin: 0 auto; padding: 0 24px;`

### Footer
- `border-top: 1px solid rgba(255,255,255,0.08); padding: 32px 24px; text-align: center;`
- Links: `color: #8b8ba3; hover: var(--gold);`

---

## Animations

### Fade Up
```css
.fade-up { opacity: 0; transform: translateY(28px); transition: opacity 0.8s ease, transform 0.8s ease; }
.fade-up.visible { opacity: 1; transform: translateY(0); }
```

### Floating Nodes
```css
@keyframes float {
  0%, 100% { transform: translateY(0) scale(1); opacity: 0.4; }
  50% { transform: translateY(-20px) scale(1.3); opacity: 0.7; }
}
/* 6 nodes: magenta, gold, teal, magenta-light, gold-light, magenta */
/* Duration: 6s ease-in-out infinite, delays: 0s, 1s, 2s, 3s, 4s, 1.5s */
```

### JS (identical all pages)
- Nav scroll threshold: 40
- IntersectionObserver: threshold 0.1, rootMargin '0px 0px -40px 0px'

---

## Responsive
- `768px`: grids → 1 column, section padding → 60px 0
- Mobile nav: hamburger (index.html only), other pages simple logo+CTA

---

## Page Accent Colors
| Page | Hero CTA | Glow | Badge |
|------|----------|------|-------|
| **index.html** | magenta | magenta+gold | gold |
| **blueprint.html** | gold | gold | gold |
| **partnerships.html** | teal | teal | teal |
| **status-manager** | magenta | magenta+gold | gold |
| **miriknows.com** | magenta | magenta+gold | gold |

### Rule: Nav CTA + Final CTA = ALWAYS magenta. Hero CTA = page accent.

---

## CSS Variables Block (copy-paste to every page)
```css
:root {
  --bg: #0a0a14;
  --bg-card: #12121e;
  --gold: #e2b21f;
  --gold-light: #f5d060;
  --magenta: #c20078;
  --magenta-light: #e84aad;
  --teal: #5b959e;
  --teal-light: #7eb8c1;
  --text: #f0f0f5;
  --text-muted: #8b8ba3;
  --text-dim: #6b7280;
  --border: rgba(255,255,255,0.08);
}
```

---

## Legacy Note
Original brand colors from Mastermind era: `#1e222c` (bg), `#e2b21f`, `#c20078`, `#5b959e`.
Updated March 2026: background darkened to `#0a0a14` to match MiriKnows premium energy.
Gold, Magenta, Teal remain unchanged.

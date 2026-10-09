# 🕐 LED Clock

A retro-styled LED clock built with pure HTML, CSS, and vanilla JavaScript — no dependencies, no build step, just open and go.

## ✨ Features

- **7-Segment Time Display** — Large, authentic seven-segment digit rendering for hours and minutes with a blinking colon separator
- **Dot-Matrix Date Display** — A hand-crafted 5×7 dot-matrix font renders the full date (e.g. `THU 09 OCT 2026`) below the time
- **Glowing Red LED Aesthetic** — Each active segment glows with layered `box-shadow` to mimic real LED luminance
- **Dark Panel Design** — Deep charcoal bezel with a subtle red radial ambient glow behind the clock
- **Live & Lightweight** — Updates every 500 ms with zero dependencies; single self-contained HTML file (~13 KB)
- **Blinking Colon** — Colon dots pulse on/off every second for authentic clock feel

## 🚀 Getting Started

No installation or build process required.

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/LED-clock.git
   cd LED-clock
   ```

2. **Open in your browser**
   ```bash
   # Simply open index.html directly
   start index.html        # Windows
   open index.html         # macOS
   xdg-open index.html     # Linux
   ```

Or just drag `index.html` into any modern web browser.

## 🗂️ Project Structure

```
LED-clock/
└── index.html   # Everything — markup, styles, and logic in one file
```

## 🔧 How It Works

### 7-Segment Display
Each digit is a `div` containing seven absolutely-positioned segment elements (top, top-left, top-right, middle, bottom-left, bottom-right, bottom). A lookup table (`SEG7`) maps each character `0–9` to a 7-bit array that toggles the `.on` class — which applies the red glow — on the appropriate segments.

### Dot-Matrix Font
The date is rendered using a fully custom 5×7 dot-matrix font encoded as binary row bitmasks. Characters supported include `A–Z`, `0–9`, `-`, and space. Each character cell is a CSS Grid of 35 tiny circular dots that are lit by toggling the `.on` class.

### Update Loop
`setInterval(tick, 500)` drives the clock. On each tick:
- The current time is read from `new Date()`
- Hours and minutes digits are updated via the segment lookup
- The date string (`DAY DD MON YYYY`) is rebuilt only if it has changed
- The colon dots toggle based on `seconds % 2`

## 🎨 Customisation

All visual properties are controlled by a handful of CSS custom values near the top of `<style>`:

| What to change | Where to look |
|---|---|
| LED colour | `.seg.on` and `.dm-dot.on` — change `#ff1a00` to any colour |
| Panel background | `.clock-panel` — `background` and `border` properties |
| Ambient glow | `body::before` — the `radial-gradient` colour stops |
| Digit size | `.digit` — `width` and `height` (segments auto-scale via `left`/`top` offsets) |
| Update rate | `setInterval(tick, 500)` — lower = faster blink |

## 🌐 Browser Support

Works in all modern browsers that support CSS Grid, `box-shadow`, and ES6.

| Browser | Support |
|---|---|
| Chrome / Edge | ✅ |
| Firefox | ✅ |
| Safari | ✅ |
| Opera | ✅ |

## 📄 License

This project is released under the [MIT License](LICENSE).

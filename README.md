# HEX → LCH Color Converter

<img width="1520" height="941" alt="Screenshot 2026-06-19 at 11 10 53" src="https://github.com/user-attachments/assets/5ed849dd-4bcc-4ce7-af3a-01e66ca46c98" />


A lightweight, zero-dependency browser tool for converting HEX colors to [CIE LCH](https://www.w3.org/TR/css-color-4/#the-lch-notation) (D65). Paste a hex value, get the perceptually uniform LCH equivalent instantly.

![Preview](https://img.shields.io/badge/no%20build%20step-open%20index.html-6c63ff?style=flat-square) ![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)

---

## Features

- **Accurate color math** — full CIE LCH D65 pipeline: HEX → sRGB → XYZ → L\*a\*b\* → LCH
- **Visual sliders** — Lightness, Chroma, and Hue displayed with gradient tracks
- **Color swatch preview** — large preview of the color on both input and output panels
- **Native color picker** — click the swatch button to pick a color from the OS picker
- **One-click copy** — copy the LCH string or HEX value to clipboard
- **Smart paste** — paste `#7ec6ff` or `7ec6ff`, both work
- **Responsive** — works on desktop and mobile
- **No dependencies** — single HTML file, works offline

---

## Usage

### Option 1 — Open directly

Clone the repo and open `index.html` in any modern browser:

```bash
git clone https://github.com/your-username/LCHConverter.git
cd LCHConverter
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

### Option 2 — Serve locally

Any static server works:

```bash
# Python
python3 -m http.server 8080

# Node (npx)
npx serve .

# VS Code
# Use the Live Server extension and click "Go Live"
```

Then visit `http://localhost:8080`.

### Option 3 — Deploy to GitHub Pages

1. Push the repo to GitHub
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch → main → / (root)**
4. Your converter will be live at `https://your-username.github.io/LCHConverter`

---

## What is LCH?

LCH (Lightness, Chroma, Hue) is a perceptually uniform color space defined by the CIE. Unlike HSL, equal numerical changes in LCH produce equal perceived differences in color, making it far more reliable for building accessible, consistent design systems.

| Channel | Range | Description |
|---------|-------|-------------|
| **L** (Lightness) | 0–100 | Perceptual brightness (0 = black, 100 = white) |
| **C** (Chroma) | 0–150+ | Colorfulness/saturation |
| **H** (Hue) | 0–360° | Angle on the color wheel |

LCH is now natively supported in CSS via the [`lch()`](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/lch) function:

```css
color: lch(77.3% 35.7 258.9);
```

---

## Color Conversion Pipeline

```
HEX → RGB → Linear RGB (gamma expanded) → XYZ D65 → L*a*b* → LCH
```

The implementation uses the standard [sRGB IEC 61966-2-1](https://www.color.org/chardata/rgb/srgb.xalter) matrix and the D65 reference white (Xn = 0.95047, Yn = 1.00000, Zn = 1.08883).

---

## Browser Support

Works in all modern browsers that support CSS backdrop-filter. No polyfills needed.

| Browser | Version |
|---------|---------|
| Chrome / Edge | 76+ |
| Firefox | 103+ |
| Safari | 15.4+ |

---

## License

[MIT](LICENSE) — free to use, modify, and share.

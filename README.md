![System 7 CSS](https://i.imgur.com/goRcNZK.png)

# System 7 CSS

A design system for building interfaces that resemble Apple's **System 7** (1991–1997), featuring the iconic grayscale 3D "chiseled" aesthetic that defined early 90s Macintosh computers.

**Inspired by [system.css](https://github.com/sakofchit/system.css)** by Sakun Acharige and **[98.css](https://github.com/jdan/98.css)** by Jordan Scales.

[![npm version](https://img.shields.io/npm/v/system7.css)](https://www.npmjs.com/package/system7.css)
[![license](https://img.shields.io/npm/l/system7.css)](LICENSE)

---

## Overview

System 7 CSS is a pure CSS library that transforms semantic HTML into authentic-looking System 7 interfaces. It requires **no JavaScript** and works with any frontend framework.

### What Makes System 7 Different?

While System 6 (the basis for system.css) used flat monochrome borders, System 7 introduced a sophisticated grayscale palette with beveled edges that create depth through light and shadow. This library faithfully recreates that aesthetic.

| Feature | system.css (System 6) | **system7.css (System 7)** |
|---------|----------------------|------------------------|
| Color Palette | Pure black & white | Grayscale with purple accents |
| Borders | SVG-based flat borders | CSS-based 3D bevels |
| Buttons | Border-image SVG | Raised 3D with rounded corners |
| Windows | Flat black outline | 3D frame with drop shadow |
| Title Bars | Black stripe pattern | Animated purple stripe pattern |
| Scrollbars | Basic styling | Full custom scrollbars with arrows |

---

## Installation

### CDN (Quickest)

```html
<link rel="stylesheet" href="https://unpkg.com/system7.css" />
```

### npm

```bash
npm install system7.css
```

```js
import 'system7.css';
```

---

## Quick Start

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>My System 7 App</title>
    <link rel="stylesheet" href="https://unpkg.com/system7.css" />
</head>
<body>
    <div class="window" style="width: 400px;">
        <div class="title-bar"> 
            <button aria-label="Close" class="close"></button>
            <h1 class="title">Welcome</h1>
            <button aria-label="Resize" class="resize"></button>
        </div>
        <div class="separator"></div>
        <div class="window-pane">
            <p>Hello from System 7!</p>
            <button class="btn btn-default">OK</button>
        </div>
    </div>
</body>
</html>
```

---

## Architecture

System 7 CSS is built with a **modular, scalable architecture** that differs significantly from the original system.css:

### Scalable Design System

All dimensions are defined relative to a single `--base-unit` variable. This allows the entire UI to be scaled proportionally by changing one value:

```css
:root {
  --base-unit: 2px;  /* Default: 1x scale */
}

/* Scale up for high-DPI displays */
:root {
  --base-unit: 4px;  /* 2x scale */
}

/* Scale down for compact UIs */
:root {
  --base-unit: 1px;  /* 0.5x scale */
}
```

**Responsive scaling example:**

```css
@media (min-width: 1200px) {
  :root {
    --base-unit: 3px; /* 1.5x on large screens */
  }
}
```

### File Structure

```
css/
├── _variables/
│   ├── _colors.css          # Base color palette
│   ├── _semantic-colors.css # Semantic color tokens
│   ├── _sizing.css          # Scalable dimensions (base-unit system)
│   └── _computed.css        # Derived/calculated values
├── _base/
│   ├── _fonts.css           # Font face definitions
│   └── _typography.css      # Base typography styles
├── _components/
│   ├── _window.css          # Window frame & panes
│   ├── _window-title-bar.css# Title bar with stripe pattern
│   ├── _window-dialog.css   # Dialog boxes (standard & modal)
│   ├── _buttons.css         # Button styles
│   ├── _forms.css           # Inputs, checkboxes, radios, selects
│   ├── _menus.css           # Menu bar & dropdown menus
│   ├── _scrollbar-thumb.css # Scrollbar track & thumb
│   └── _scrollbar-arrows.css# Scrollbar arrow buttons & corner
└── _utilities/
    └── _patterns.css        # Desktop pattern utility
```

### CSS Custom Properties

The library exposes a comprehensive set of CSS variables for theming:

#### Colors
```css
:root {
  /* Base palette */
  --color-white: #FFFFFF;
  --color-black: #000000;
  --color-gray-100 through --color-gray-800;
  --color-purple-100 through --color-purple-700;
  
  /* Semantic tokens */
  --surface: #dadada;           /* Window/dialog backgrounds */
  --surface-header: #f1f1f1;    /* Title bar background */
  --border-active: #000000;     /* Active window borders */
  --border-inactive: #555555;   /* Inactive window borders */
  --text-color: #000000;
  --text-disabled: #808080;
}
```

#### Sizing
```css
:root {
  --base-unit: 2px;             /* Master scale unit */
  --border-width: calc(1 * var(--base-unit));
  --title-bar-height: calc(15 * var(--base-unit));
  --scrollbar-button-size: calc(14 * var(--base-unit));
  /* ... and many more */
}
```

---

## Components

### Windows

```html
<!-- Active Window -->
<div class="window">
    <div class="title-bar">
        <button aria-label="Close" class="close"></button>
        <h1 class="title">Window Title</h1>
        <button aria-label="Resize" class="resize"></button>
    </div>
    <div class="separator"></div>
    <div class="details-bar">
        <span>3 items</span>
        <span>2.1 MB available</span>
    </div>
    <div class="window-pane">
        Content goes here
    </div>
</div>

<!-- Inactive Window -->
<div class="window inactive">
    <div class="inactive-title-bar">
        <button aria-label="Close" class="close"></button>
        <h1 class="title">Inactive Window</h1>
        <button aria-label="Resize" class="resize"></button>
    </div>
    <div class="separator"></div>
    <div class="window-pane">...</div>
</div>
```

### Scrollbar States

```html
<!-- Window with disabled vertical scrollbar -->
<div class="window no-scroll-v">...</div>

<!-- Window with disabled horizontal scrollbar -->
<div class="window no-scroll-h">...</div>

<!-- Window with both scrollbars disabled -->
<div class="window no-scroll">...</div>
```

### Buttons

```html
<button class="btn">Standard</button>
<button class="btn btn-default">Default (Primary)</button>
<button class="btn" disabled>Disabled</button>
```

### Dialogs

```html
<!-- Standard Dialog -->
<div class="standard-dialog">
    <p>This is a standard dialog.</p>
    <button class="btn btn-default">OK</button>
</div>

<!-- Modal Dialog (with ornate border) -->
<div class="modal-dialog">
    <div class="modal-dialog-content">
        <p>This is a modal alert!</p>
        <button class="btn btn-default">OK</button>
    </div>
</div>
```

### Form Controls

```html
<!-- Text Input -->
<input type="text" placeholder="Enter text...">

<!-- Checkbox -->
<div class="field-row">
    <input id="chk1" type="checkbox">
    <label for="chk1">Enable feature</label>
</div>

<!-- Radio Buttons -->
<div class="field-row">
    <input id="rad1" type="radio" name="options">
    <label for="rad1">Option A</label>
</div>
<div class="field-row">
    <input id="rad2" type="radio" name="options">
    <label for="rad2">Option B</label>
</div>

<!-- Select Dropdown -->
<div class="select-wrapper">
    <select>
        <option>Choose...</option>
        <option>Option 1</option>
        <option>Option 2</option>
    </select>
</div>
```

### Menus

```html
<ul role="menu-bar">
    <li role="menu-item" class="apple" aria-haspopup="false"></li>
    <li role="menu-item" tabindex="0" aria-haspopup="true">
        File
        <ul role="menu">
            <li role="menu-item"><a href="#">New</a></li>
            <li role="menu-item"><a href="#">Open...</a></li>
            <li role="separator"></li>
            <li role="menu-item" aria-disabled="true"><a href="#">Save</a></li>
        </ul>
    </li>
    <li role="menu-item" tabindex="0" aria-haspopup="true">
        Edit
        <ul role="menu">
            <li role="menu-item"><a href="#">Cut</a></li>
            <li role="menu-item"><a href="#">Copy</a></li>
            <li role="menu-item"><a href="#">Paste</a></li>
        </ul>
    </li>
</ul>
```

---

## Key Differences from system.css

This project started as a fork of system.css but has evolved with significant architectural changes:

### 1. **Scalable Base Unit System**
All pixel values are expressed as multiples of `--base-unit`, allowing the entire UI to scale proportionally. system.css uses fixed pixel values throughout.

### 2. **Modular File Architecture**
CSS is organized into logical modules (`_variables`, `_base`, `_components`, `_utilities`) instead of a single monolithic file.

### 3. **Semantic Color Tokens**
Colors are defined in two layers: a base palette and semantic tokens that reference them. This makes theming more maintainable.

### 4. **SVG-Based Scrollbar Arrows**
Complex scrollbar arrows are implemented as SVG files rather than CSS gradients, reducing code complexity and improving maintainability.

### 5. **CSS-Only 3D Effects**
Where system.css relies on SVG border-images for buttons and controls, system7.css achieves 3D effects primarily through CSS `box-shadow` layering.

### 6. **Complete Scrollbar Styling**
Fully custom WebKit scrollbars with:
- Textured track patterns
- 3D thumb with stripe decoration
- Arrow buttons with normal, active, and disabled states
- Resize corner handle

---

## Development

### Setup

```bash
git clone https://github.com/feedforfools/system7.css.git
cd system7.css
npm install
```

### Build

```bash
npm run build
```

This compiles all CSS modules into `dist/system7.css`.

### Playground

Open `playground/index.html` in your browser to preview all components.

---

## Browser Support

- **Chrome/Edge**: Full support (including custom scrollbars)
- **Firefox**: Full support (scrollbars use default styling)
- **Safari**: Full support (including custom scrollbars)

Custom scrollbar styling uses WebKit-specific pseudo-elements (`::-webkit-scrollbar-*`). Firefox will display native scrollbars.

---

## Credits

- **system.css** by [Sakun Acharige](https://github.com/sakofchit/system.css) — Original inspiration
- **98.css** by [Jordan Scales](https://github.com/jdan/98.css) — 3D border techniques
- **Fonts**: Chicago 12pt and Geneva 9pt recreations by [@blogmywiki](https://twitter.com/blogmywiki)

---

## License

[MIT](LICENSE)

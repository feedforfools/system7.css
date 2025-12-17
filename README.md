
![System 7 CSS](https://i.imgur.com/goRcNZK.png)

# System 7 CSS

A CSS library for building interfaces that resemble Apple's **System 7** (MacOS 7), featuring the iconic grayscale 3D "chiseled" aesthetic that defined early 90s Macintosh computers.

**Based on [system.css](https://github.com/sakofchit/system.css) by Sakun Acharige**, with 3D border techniques adapted from [98.css](https://github.com/jdan/98.css) by Jordan Scales.

## What is System 7 CSS?

System 7 CSS transforms the monochrome System 6 aesthetic into the grayscale 3D look of System 7. While System 6 used flat black-and-white borders, System 7 introduced beveled edges that create a sense of depth through light and shadow.

### Key Differences from system.css

| Feature | system.css (System 6) | system7.css (System 7) |
|---------|----------------------|------------------------|
| **Color Palette** | Pure black & white (#000/#FFF) | Grayscale palette (#dadada surface) |
| **Borders** | SVG-based flat borders | CSS box-shadow 3D bevels |
| **Buttons** | Border-image SVG | Raised 3D effect with rounded corners |
| **Windows** | Flat black outline | 3D window frame with drop shadow |
| **Title Bars** | Black stripe pattern | Gray (placeholder for stripe pattern) |
| **Inputs** | Flat border | Sunken 3D field effect |

## Getting Started

### Import from CDN

Add the following to your `<head>` tag:

```html
<link rel="stylesheet" href="https://unpkg.com/system7.css" />
```

### Install from npm

```bash
npm install system7.css
```

### Starter Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>System 7 CSS Starter</title>
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="https://unpkg.com/system7.css" />
</head>
<body>
    <div class="window" style="width:30rem;">
        <div class="title-bar"> 
            <button aria-label="Close" class="close"></button>
            <h1 class="title">System 7</h1>
            <button aria-label="Resize" class="resize"></button>
        </div>
        <div class="separator"></div>
        
        <div class="window-pane">
            Hello from System 7!
        </div>
    </div>
</body>
</html>
```

## Components

### Windows

```html
<div class="window">
    <div class="title-bar">
        <button aria-label="Close" class="close"></button>
        <h1 class="title">Window Title</h1>
        <button aria-label="Resize" class="resize"></button>
    </div>
    <div class="separator"></div>
    <div class="window-pane">
        Window content goes here
    </div>
</div>
```

### Buttons

```html
<button class="btn">Standard Button</button>
<button class="btn btn-default">Default Button</button>
<button class="btn" disabled>Disabled Button</button>
```

### Dialogs

```html
<div class="standard-dialog">
    <h1 class="dialog-text">Dialog Title</h1>
    <p class="dialog-text">Dialog content</p>
</div>
```

### Form Elements

```html
<!-- Text Input -->
<input type="text" placeholder="Enter text...">

<!-- Checkbox -->
<div class="field-row">
    <input id="chk1" type="checkbox">
    <label for="chk1">Checkbox option</label>
</div>

<!-- Radio Buttons -->
<div class="field-row">
    <input id="rad1" type="radio" name="group1">
    <label for="rad1">Option 1</label>
</div>
```

## Development

1. Clone the repository: `git clone https://github.com/feedforfools/system7.css.git`
2. Install dependencies: `npm install`
3. Build: `npm run build`

### Playground

Open `playground/index.html` in your browser to preview all components with the System 7 styling.

## Architecture

### CSS Variables

System 7 CSS uses CSS custom properties for theming:

```css
:root {
    --surface: #dadada;           /* Main background color */
    --button-face: #dadada;       /* Button surface */
    --button-highlight: #ffffff;  /* Light edge (3D highlight) */
    --button-shadow: #808080;     /* Dark edge (3D shadow) */
    --window-frame: #000000;      /* Window borders */
    
    /* 3D Border Composites */
    --border-raised-outer: ...;   /* Raised element outer shadow */
    --border-raised-inner: ...;   /* Raised element inner shadow */
    --border-sunken-outer: ...;   /* Sunken element outer shadow */
    --border-sunken-inner: ...;   /* Sunken element inner shadow */
}
```

### 3D Border System

The 3D effect is achieved through carefully layered `box-shadow` values:

- **Raised elements** (buttons, windows): Light top-left edges, dark bottom-right edges
- **Sunken elements** (inputs, pressed buttons): Dark top-left edges, light bottom-right edges

## Roadmap / Human Tasks

The following items are placeholders that require manual asset creation:

1. **Title Bar Stripes**: The active title bar currently uses a solid gray. The authentic 6-stripe horizontal pattern needs to be added.
2. **Icons**: Pixel-art icons (Folder, Trash, etc.) need to be created in color.
3. **Desktop Pattern**: The classic checkerboard desktop pattern.

## Credits

- **Original system.css**: [Sakun Acharige](https://github.com/sakofchit/system.css)
- **3D Border Techniques**: Adapted from [98.css](https://github.com/jdan/98.css) by [Jordan Scales](https://github.com/jdan)
- **Fonts**: Chicago 12pt and Geneva 9pt recreations by [@blogmywiki](https://twitter.com/blogmywiki)

## License

MIT License - see [LICENSE](LICENSE) for details.

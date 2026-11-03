# 📦 fonts-cdn

Self-hosted font CDN for my portfolio and projects.
Packaged with `@font-face` rules so you can drop one CSS link and start using custom fonts without relying on Google Fonts.

---

## 🚀 Usage

### 1. Add the CSS

Include the CDN stylesheet in your `<head>`:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/atharvwasthere/fonts-cdn@v1.1.0/fonts.css"
/>
```

> ✅ Version is pinned (`@v1.1.0`) for stability.
> Use `@latest` if you want to always pull the newest release.

---

### 2. Use fonts in CSS

Fonts included:

```css
body {
  font-family: "Satoshi", sans-serif;
}

h1, h2 {
  font-family: "Zodiak", serif;
}

.logo {
  font-family: "Autography", cursive;
}

.nav {
  font-family: "Cabinet Grotesk", sans-serif;
}

.tagline {
  font-family: "Segment", system-ui, sans-serif;
}
```

---

## 📂 Available Fonts

* **Autography** → Regular
* **Cabinet Grotesk** → Variable weight (100–900)
* **Satoshi** → Variable (Normal + Italic, 300–900)
* **Segment** → Regular
* **Zodiak** → Variable (Normal + Italic, 100–900)
* **Geist Serif** → Regular only, no italic (Vercel, SIL OFL; licence in `fonts/GeistSerif/OFL.txt`)

---

## ⚡ Notes

* Fonts are served via **JSDelivr CDN** for speed + cacheability.
* Use `font-display: swap;` → ensures text is visible during load.
* Variable fonts expose their full weight range (100–900).

---

## 🔮 Example (with preload)

If you want faster first paint, preload your main font:

```html
<link
  rel="preload"
  href="https://cdn.jsdelivr.net/gh/atharvwasthere/fonts-cdn@v1.1.0/fonts/satoshi/Satoshi-Variable.woff2"
  as="font" type="font/woff2" crossorigin="anonymous"
/>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/atharvwasthere/fonts-cdn@v1.1.0/fonts.css"
/>
```

---

## 🛠️ Contribution Guide

### 1. Add a new font

* Create a new folder under `/fonts/<FontName>`
* Add `.woff2` (preferred) and `.woff` versions of the font.

Example:

```
fonts/
 └── MyNewFont/
     ├── MyNewFont-Regular.woff2
     ├── MyNewFont-Regular.woff
     ├── MyNewFont-Bold.woff2
     └── MyNewFont-Bold.woff
```

### 2. Update `fonts.css`

Add an `@font-face` block for your new font:

```css
@font-face {
  font-family: "My New Font";
  src: url("./fonts/MyNewFont/MyNewFont-Regular.woff2") format("woff2"),
       url("./fonts/MyNewFont/MyNewFont-Regular.woff") format("woff");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

> ⚠️ Keep URLs **relative** (`./fonts/...`). They resolve against the tag `fonts.css` was loaded from, so a new release needs no URL edits.

### 3. Bump version

* Update version number in README examples.
* Tag a new release in Git (`git tag v1.2.0 && git push origin v1.2.0`).
* JSDelivr will automatically serve the new version.

### 4. Test it

* Open your site, check browser devtools → Network → Fonts.
* Make sure the new font loads from CDN and applies correctly.

---

👉 With this, your `fonts-cdn` repo becomes a **mini Google Fonts, but self-hosted** — clean, predictable, and under your control.

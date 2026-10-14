<div align="center">

# 🎨 CSS Fundamentals: Filters, Object-Fit & Backgrounds

**Two experiments on restyling images and controlling how they fit inside a box, all in CSS and without editing the image files**

</div>

---

## 📖 About This Repository

This repository contains mini-projects I built while learning CSS. Each folder holds a single `index.html` file, so every concept is easy to see, edit, and experiment with.

No frameworks, no build tools, no image editing. Just HTML and CSS.

---

## 📑 Table of Contents

1. [Project Structure](#-project-structure)
2. [Experiment 1: CSS Filters](#-experiment-1-css-filters)
3. [Experiment 2: Object-Fit, Object-Position & Backgrounds](#-experiment-2-object-fit-object-position--backgrounds)
4. [`<img>` or `background-image`?](#-img-or-background-image)
5. [How to Run](#-how-to-run)
6. [Key Takeaways](#-key-takeaways)
7. [Roadmap](#-roadmap)

---

## 📂 Project Structure

```
css-fundamentals/
│
├── 23-css-filters/
│   └── index.html
│
├── 24-object-fit-backgrounds/
│   └── index.html
│
└── README.md
```

> 💡 Rename the folders to match your own layout. Each `index.html` is fully standalone.

---

## 🎞️ Experiment 1: CSS Filters

📁 `23-css-filters/index.html`

### 🎯 Goal
Apply Photoshop-style effects to images using a single CSS property, and learn how to combine them.

### 🧱 The Setup

Three images sit inside one container, and each gets a different filter:

```html
<div class="container">
  <img class="img1" src="..." alt="">
  <img class="img2" src="..." alt="">
  <img class="img3" src="..." alt="">
</div>
```

### 🧪 Code Highlight

```css
/* img { filter: blur(10px); } */

.img1 {
  filter: brightness(122%) contrast(0.5);
}

.img2 {
  filter: grayscale(20%);
}

.img3 {
  filter: sepia(20%);
}
```

### 🔑 The Filter Functions

<table>
  <tr>
    <th>Function</th>
    <th>Example</th>
    <th>Effect</th>
    <th>Neutral value</th>
  </tr>
  <tr>
    <td><code>blur()</code></td>
    <td><code>blur(10px)</code></td>
    <td>Softens the element. Takes a length, not a percentage.</td>
    <td align="center"><code>0</code></td>
  </tr>
  <tr>
    <td><code>brightness()</code></td>
    <td><code>brightness(122%)</code></td>
    <td>Lightens (above 100%) or darkens (below 100%).</td>
    <td align="center"><code>100%</code> or <code>1</code></td>
  </tr>
  <tr>
    <td><code>contrast()</code></td>
    <td><code>contrast(0.5)</code></td>
    <td>Below 1 flattens the image; above 1 makes it punchier.</td>
    <td align="center"><code>100%</code> or <code>1</code></td>
  </tr>
  <tr>
    <td><code>grayscale()</code></td>
    <td><code>grayscale(20%)</code></td>
    <td>Removes color. <code>100%</code> is fully black and white.</td>
    <td align="center"><code>0</code></td>
  </tr>
  <tr>
    <td><code>sepia()</code></td>
    <td><code>sepia(20%)</code></td>
    <td>Adds a warm, vintage brown tone.</td>
    <td align="center"><code>0</code></td>
  </tr>
  <tr>
    <td><code>saturate()</code></td>
    <td><code>saturate(200%)</code></td>
    <td>Boosts or reduces color intensity.</td>
    <td align="center"><code>100%</code></td>
  </tr>
  <tr>
    <td><code>hue-rotate()</code></td>
    <td><code>hue-rotate(90deg)</code></td>
    <td>Shifts every color around the color wheel.</td>
    <td align="center"><code>0deg</code></td>
  </tr>
  <tr>
    <td><code>invert()</code></td>
    <td><code>invert(100%)</code></td>
    <td>Flips colors to their opposites, like a photo negative.</td>
    <td align="center"><code>0</code></td>
  </tr>
  <tr>
    <td><code>opacity()</code></td>
    <td><code>opacity(50%)</code></td>
    <td>Makes the element see-through.</td>
    <td align="center"><code>100%</code></td>
  </tr>
  <tr>
    <td><code>drop-shadow()</code></td>
    <td><code>drop-shadow(4px 4px 6px black)</code></td>
    <td>A shadow that follows the <b>visible shape</b> of the element, including transparent areas in PNGs.</td>
    <td align="center">n/a</td>
  </tr>
</table>

### 🧠 What Happens Here

<table>
  <tr>
    <td>1️⃣</td>
    <td><code>.img1</code> chains two filters: <code>brightness(122%)</code> lightens it, then <code>contrast(0.5)</code> cuts the contrast to half. The result is a bright, washed-out look.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td><code>.img2</code> removes only 20% of the color, so it looks slightly muted rather than black and white.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td><code>.img3</code> adds a light 20% sepia tint, a subtle warm tone.</td>
  </tr>
  <tr>
    <td>4️⃣</td>
    <td>Percentages and decimals are interchangeable: <code>contrast(0.5)</code> is the same as <code>contrast(50%)</code>.</td>
  </tr>
</table>

### 🔗 Chaining Filters

Multiple filters go in one `filter` declaration, separated by spaces. They are applied **from left to right**, and the order can change the result:

```css
filter: brightness(1.2) contrast(0.5);   /* brighten first, then flatten */
filter: contrast(0.5) brightness(1.2);   /* flatten first, then brighten */
```

> ⚠️ Writing two separate `filter` lines does **not** combine them. The second one replaces the first.

### 📝 Good to Know

<table>
  <tr>
    <td>💡</td>
    <td>Filters work on <b>any element</b>, not just images. Try one on a button, a card, or a whole section.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>Like <code>transform</code>, a filter changes how an element <b>looks</b> but does not change the layout around it.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td><code>filter</code> is animatable, so it works beautifully with <code>transition</code>.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td><code>backdrop-filter: blur(10px)</code> blurs what is <b>behind</b> an element instead of the element itself. This is the "frosted glass" effect.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td><code>drop-shadow()</code> follows the shape of an image. <code>box-shadow</code> always draws a rectangle.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>An element with a <code>filter</code> becomes the reference point for its <code>absolute</code> and <code>fixed</code> children, just like a <code>transform</code> does.</td>
  </tr>
</table>

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>Empty <code>alt</code> text:</b> <code>alt=""</code> tells screen readers to skip the image. That is correct only for purely decorative images. Meaningful images need a description.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Hotlinked thumbnails:</b> image links from search engines (such as <code>encrypted-tbn0.gstatic.com</code>) can stop loading at any time. Use local files or a stable image host.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>No sizing:</b> the images have no width or height, so they appear at their natural size. Add <code>width</code> and <code>max-width: 100%</code> for a responsive layout.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Heavy blur on large areas</b> can slow down low-powered devices.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Uncomment `img { filter: blur(10px); }` and watch all three images blur at once. Notice how `.img1`, `.img2`, and `.img3` override it, because class selectors are more specific than element selectors.
2. Raise `grayscale(20%)` to `100%` for full black and white.
3. Try `sepia(100%)` for a strong old-photo look.
4. Add a hover effect that fades the color back in:

```css
img {
  filter: grayscale(100%);
  transition: filter 0.4s;
}

img:hover {
  filter: grayscale(0);
}
```

5. Swap the order of `brightness()` and `contrast()` in `.img1` and compare the results.
6. Chain several filters: `filter: sepia(60%) saturate(140%) hue-rotate(-10deg);`.
7. Try `invert(100%)` on a dark-themed icon to switch it to light.

</details>

### 📚 Filter Cheat Sheet

| Goal | Use |
|---|---|
| Black-and-white image | `filter: grayscale(100%);` |
| Vintage look | `filter: sepia(60%) contrast(1.1);` |
| Dim an image behind text | `filter: brightness(50%);` |
| Soften a background | `filter: blur(8px);` |
| Shadow that follows a PNG's shape | `filter: drop-shadow(4px 4px 6px rgba(0,0,0,.4));` |
| Frosted glass panel | `backdrop-filter: blur(10px);` |
| Smooth hover effect | `transition: filter 0.3s;` |

---

## 🖼️ Experiment 2: Object-Fit, Object-Position & Backgrounds

📁 `24-object-fit-backgrounds/index.html`

### 🎯 Goal
Control how an image fits inside a box of a different shape, and understand how **background images** behave on a container.

### 🧪 Code Highlight

```css
.container {
  height: 488px;
  width: 466px;
  border: 2px solid black;
  background-image: url("...");
  background-position: center center;
  /* background-repeat: no-repeat; */
  background-clip: border-box;
}

img {
  width: 466px;
  height: 488px;
  object-fit: contain;
  /* object-position: bottom right; */
}
```

### 🔑 Part A: `object-fit` Values

When an `<img>` is forced into a box whose shape differs from the image, `object-fit` decides what to do.

<table>
  <tr>
    <th>Value</th>
    <th>Behavior</th>
    <th>Keeps aspect ratio?</th>
    <th>Crops?</th>
    <th>Leaves empty space?</th>
  </tr>
  <tr align="center">
    <td><code>fill</code> (default)</td>
    <td align="left">Stretches the image to fill the box exactly</td>
    <td>❌ No (distorts)</td>
    <td>No</td>
    <td>No</td>
  </tr>
  <tr align="center">
    <td><code>contain</code></td>
    <td align="left">Scales the image to fit entirely inside the box</td>
    <td>✅ Yes</td>
    <td>No</td>
    <td>Yes</td>
  </tr>
  <tr align="center">
    <td><code>cover</code></td>
    <td align="left">Scales the image to cover the whole box</td>
    <td>✅ Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
  <tr align="center">
    <td><code>none</code></td>
    <td align="left">Keeps the image's original size</td>
    <td>✅ Yes</td>
    <td>If larger than the box</td>
    <td>If smaller than the box</td>
  </tr>
  <tr align="center">
    <td><code>scale-down</code></td>
    <td align="left">Whichever is smaller: <code>none</code> or <code>contain</code></td>
    <td>✅ Yes</td>
    <td>No</td>
    <td>Maybe</td>
  </tr>
</table>

> 💡 `object-fit` works on **replaced elements** such as `<img>` and `<video>`, not on regular `<div>` elements.

### 🔑 Part B: `object-position`

`object-position` chooses **which part of the image** stays visible or where it sits inside the box. It only shows a difference when the image does not fill the box exactly (for example with `contain`, `cover`, or `none`).

<table>
  <tr>
    <th>Value</th>
    <th>Meaning</th>
  </tr>
  <tr>
    <td><code>50% 50%</code> (default)</td>
    <td>Centered</td>
  </tr>
  <tr>
    <td><code>bottom right</code></td>
    <td>Pinned to the bottom-right corner</td>
  </tr>
  <tr>
    <td><code>top</code></td>
    <td>Keep the top of the image visible (great for portraits with <code>cover</code>)</td>
  </tr>
  <tr>
    <td><code>10px 20px</code></td>
    <td>Offset 10px from the left and 20px from the top</td>
  </tr>
</table>

### 🔑 Part C: Background Properties Used

<table>
  <tr>
    <th>Property</th>
    <th>Example</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>background-image</code></td>
    <td><code>url("...")</code></td>
    <td>Sets an image as the element's background.</td>
  </tr>
  <tr>
    <td><code>background-position</code></td>
    <td><code>center center</code></td>
    <td>Where the image sits inside the box.</td>
  </tr>
  <tr>
    <td><code>background-repeat</code></td>
    <td><code>no-repeat</code></td>
    <td>Whether the image tiles. <b>The default is to repeat</b> in both directions.</td>
  </tr>
  <tr>
    <td><code>background-clip</code></td>
    <td><code>border-box</code></td>
    <td>How far the background extends. <code>border-box</code> (default) goes underneath the border; <code>padding-box</code> stops at the border; <code>content-box</code> stops at the padding.</td>
  </tr>
  <tr>
    <td><code>background-size</code></td>
    <td><code>cover</code>, <code>contain</code>, <code>200px</code></td>
    <td>Sizes the background. Not used in this demo, but essential. The default is <code>auto</code> (the image's natural size).</td>
  </tr>
</table>

### 🧠 What Happens in the Demo

<table>
  <tr>
    <td>1️⃣</td>
    <td>The container is <code>466px × 488px</code> with a 2px border. Because there is no <code>box-sizing: border-box</code>, the border is added on top, making the box 470px × 492px overall.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td>The visible picture is the container's <b>background image</b>, centered with <code>background-position: center center</code>.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td>With <code>background-repeat</code> commented out, an image smaller than the box <b>tiles</b>. An image larger than the box is cropped, because <code>background-size</code> is the default <code>auto</code>.</td>
  </tr>
  <tr>
    <td>4️⃣</td>
    <td>The <code>&lt;img&gt;</code> is commented out in the HTML, so the <code>img</code> rule (including <code>object-fit</code>) currently has nothing to style. When you uncomment the image, its <code>466px × 488px</code> size matches the container's content area exactly.</td>
  </tr>
</table>

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>An invalid <code>object-fit</code> value:</b> <code>object-fit: 10px 20px;</code> is not valid. <code>object-fit</code> only accepts <code>fill</code>, <code>contain</code>, <code>cover</code>, <code>none</code>, or <code>scale-down</code>. Position offsets like <code>10px 20px</code> belong to <b><code>object-position</code></b>. Browsers silently ignore the invalid line, so an earlier valid value keeps working and hides the mistake.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Duplicate declarations:</b> <code>object-fit: contain;</code> appears twice (once active, once commented). Keep one.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Testing the wrong thing:</b> with the <code>&lt;img&gt;</code> commented out, changing <code>object-fit</code> shows no change.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Surprise tiling:</b> forgetting <code>background-repeat: no-repeat</code> makes small images repeat.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Hotlinked thumbnails</b> can disappear. Use local images for anything you want to keep.</td>
  </tr>
</table>

### ✅ Corrected Version

```css
img {
  width: 466px;
  height: 488px;
  object-fit: contain;
  object-position: bottom right;   /* offsets belong here */
}
```

And for the background version, add the missing pieces:

```css
.container {
  background-image: url("...");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
```

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Uncomment the `<img>` in the HTML so the `img` rules take effect.
2. Cycle `object-fit` through `fill`, `contain`, `cover`, `none`, and `scale-down` and compare how the image changes.
3. With `object-fit: contain` or `cover`, add `object-position: bottom right;` and then `top left;`.
4. Try `object-position: 10px 20px;` (the value you originally had in `object-fit`) with `object-fit: none`.
5. Uncomment `background-repeat: no-repeat;` and see the tiling stop.
6. Add `background-size: cover;`, then `contain`, and compare them with the `object-fit` results.
7. Change `background-clip: border-box` to `content-box` and make the border `20px dashed` to see where the background stops.
8. Combine with Experiment 1: add `filter: grayscale(100%);` to the image.

</details>

---

## 🤔 `<img>` or `background-image`?

<table>
  <tr>
    <th></th>
    <th><code>&lt;img&gt;</code> + <code>object-fit</code></th>
    <th><code>background-image</code> + <code>background-size</code></th>
  </tr>
  <tr>
    <td><b>Best for</b></td>
    <td>Content images: photos, products, articles</td>
    <td>Decoration: patterns, hero backgrounds, textures</td>
  </tr>
  <tr>
    <td><b>Accessibility</b></td>
    <td>✅ Supports <code>alt</code> text</td>
    <td>❌ No alt text, invisible to screen readers</td>
  </tr>
  <tr>
    <td><b>Lazy loading</b></td>
    <td>✅ <code>loading="lazy"</code></td>
    <td>Not built in</td>
  </tr>
  <tr>
    <td><b>Responsive images</b></td>
    <td>✅ <code>srcset</code> and <code>sizes</code></td>
    <td>Possible with media queries or <code>image-set()</code></td>
  </tr>
  <tr>
    <td><b>Printing</b></td>
    <td>Prints by default</td>
    <td>Often not printed by default</td>
  </tr>
  <tr>
    <td><b>Fit equivalent</b></td>
    <td><code>object-fit: cover</code></td>
    <td><code>background-size: cover</code></td>
  </tr>
  <tr>
    <td><b>Position equivalent</b></td>
    <td><code>object-position</code></td>
    <td><code>background-position</code></td>
  </tr>
</table>

> 💡 **Rule of thumb:** if the image carries meaning, use `<img>`. If it is only decoration, use a background.

---

## 🚀 How to Run

No installation needed.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git

# 2. Move into the project
cd <your-repo-name>

# 3. Open any experiment in your browser
open 23-css-filters/index.html      # macOS
start 23-css-filters/index.html     # Windows
xdg-open 23-css-filters/index.html  # Linux
```

💡 **Tip:** Replace the hotlinked image URLs with local files (for example `./images/photo1.jpg`) so the demos keep working offline. Use the VS Code **Live Server** extension to see changes instantly.

---

## 🎓 Key Takeaways

<table>
  <tr>
    <td>✅</td>
    <td><code>filter</code> restyles images (and any other element) without touching the original file.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Filters chain from left to right, and order can change the look. Two separate <code>filter</code> lines don't combine.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>filter</code> is animatable, so pairing it with <code>transition</code> gives easy hover effects.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>object-fit</code> chooses how an image fits its box: <code>fill</code> distorts, <code>contain</code> shows everything, <code>cover</code> fills and crops.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>object-position</code>, not <code>object-fit</code>, takes offsets like <code>10px 20px</code> or keywords like <code>bottom right</code>.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Invalid CSS is ignored silently, so a typo may hide in plain sight. DevTools shows struck-through invalid lines.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Background images tile by default. Use <code>background-repeat</code> and <code>background-size</code> to control them.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Use <code>&lt;img&gt;</code> for content and <code>background-image</code> for decoration.</td>
  </tr>
</table>

---

## 🗺️ Roadmap

- [x] `display` property
- [x] Viewport units and box model
- [x] CSS specificity
- [x] `overflow`
- [x] Lists and `list-style`
- [x] `box-shadow` and `text-shadow`
- [x] Positioning (`relative`, `absolute`, `fixed`, `sticky`)
- [x] Card component
- [x] Media queries
- [x] CSS variables
- [x] Landing page project
- [x] Float and clear
- [x] Pseudo-elements and advanced selectors
- [x] Full page layout with sticky navbar
- [x] Flexbox fundamentals
- [x] CSS Grid fundamentals and template areas
- [x] Responsive grid download page
- [x] CSS transforms
- [x] CSS transitions
- [x] Keyframe animations
- [x] CSS filters
- [x] `object-fit`, `object-position`, and background images
- [ ] Image hover gallery combining `filter` and `transition`
- [ ] CSS gradients
- [ ] Rebuild the bouncing ball using `transform`
- [ ] Responsive project combining Flexbox, Grid, media queries, and animation
- [ ] Grid auto-placement (`grid-auto-flow`, `grid-auto-rows`)
- [ ] Mobile-first workflow

---

<div align="center">

### ⭐ If you found this helpful, consider giving the repo a star!

Made with ❤️ while learning CSS

</div>

# Auto Grouping with Add Component

A small, single-file HTML/JavaScript demo that lets you **drag boxes** inside a canvas, **auto-group** them when they are close to each other, and generates a **live HTML output** showing the current grouping structure. This repo is intentionally lightweight for easy sharing and experimentation.

---

## ✨ Features

* Draggable boxes that you can move around freely.
* Automatic grouping of boxes based on a configurable proximity threshold.
* Visual bounding boxes to highlight groups (when group size > 1).
* Live HTML output panel showing the grouped structure.
* Add new components dynamically with a button.
* Single-file distribution (`index.html`) for quick testing.

---

## 📁 Project Structure

```
index.html        # Main HTML file (contains CSS and JavaScript)
README.md         # This file
```

> All logic, styles, and markup are bundled in `index.html` so you can drop it into any static host or open it locally.

---

## 🚀 Quick Start

1. Clone the repository or download the files.

```bash
git clone <your-repo-url>
cd <repo-folder>
```

2. Open `index.html` in a modern web browser (Chrome, Firefox, Edge, Safari).
3. Drag the boxes inside the canvas. Add new components using the **Add Component** button.

---

## ⚙ Configuration

You can tweak grouping sensitivity by editing the threshold value in the script inside `index.html`:

```js
const THRESHOLD = 150; // px — distance in pixels for grouping
```

Lower values require objects to be closer to form a group; higher values make grouping more permissive.

---

## 🛠 How It Works (Overview)

* **Draggable behavior**: Each element with the `.draggable` class receives mouse event listeners (`mousedown`, `mousemove`, `mouseup`) that update `left` and `top` styles as you drag.

* **Grouping logic**: After each movement (and when new components are added), the script collects all `.draggable` elements and forms groups by checking pairwise proximity using `isNearby()`.

* **Proximity detection**: `isNearby(el1, el2)` uses DOM `getBoundingClientRect()` to measure positions. If both the X and Y differences are less than `THRESHOLD`, the elements are considered in the same group.

* **Group visualization**: For groups with more than one element, the script computes a bounding box (`getBoundingBox`) and renders a `.group-highlight` element on the canvas to visualize the group.

* **Live HTML output**: `updateOutput()` recomputes groups and emits a simple HTML representation of the grouping structure into the right-side panel.

---

## ✅ Browser Support

This demo uses standard DOM APIs and should work on all modern browsers. For best experience, use the latest version of Chrome, Firefox, Edge, or Safari.

---

## ♻️ Extending & Improvements (Ideas)

Here are suggestions if you want to expand the project:

* Persist layouts to JSON and allow import/export.
* Add keyboard accessibility for moving/selecting boxes.
* Support touch events for mobile drag-and-drop.
* Add resize handles so boxes can change size.
* Improve grouping to use Euclidean (diagonal) distance rather than separate X/Y thresholds.
* Allow nested groups and collapse/expand controls.
* Provide an “Export grouped HTML” download button.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! If you want to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-change`)
3. Commit your changes (`git commit -m "feat: add ..."`)
4. Push to the branch (`git push origin feature/your-change`)
5. Open a Pull Request describing your changes

Please keep changes focused and add comments where appropriate.

---

## 📝 License

This project is released under the **MIT License**. See the `LICENSE` file for details (or add one to the repo if you haven’t yet).

---

## ✉️ Author / Contact

If you want help improving this demo or want me to generate additional assets (demo GIF, code-splitting into separate files, or a small build setup), just tell me what you'd like and I’ll help.

---

*Happy prototyping!*

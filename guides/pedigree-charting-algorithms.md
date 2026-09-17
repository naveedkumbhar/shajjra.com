# 📊 Pedigree Charting & Tree Visualization Algorithms

> Architectural and algorithmic blueprints for rendering large-scale (1,000+ node) genealogical pedigree charts and interactive family trees on the web.

---

## 1. Visualizing Deep Genealogies

Rendering 45 generations of genealogical data poses distinct algorithmic challenges:
1. **Geometric Expansion:** In a binary ancestor chart ($2^n$), generation 10 requires $1,024$ slots; generation 45 would mathematically require trillions of theoretical ancestor slots without pedigree collapse.
2. **DOM Bottlenecks:** Rendering thousands of individual HTML node elements crushes browser framerates on mobile devices.
3. **Responsive Connectors:** Line connectors between parents and children must dynamically recalculate on viewport resize and canvas pan/zoom.

---

## 2. The 3 Charting Models Implemented on Shajjra.com

### Model A: 5-Generation Focused Pedigree Chart
Rather than rendering the entire universe on a single flat screen, the pedigree view centers on a single subject and renders their immediate ancestral trajectory:

```
[ Father's Paternal Grandfather ] ──┐
                                     ├── [ Paternal Grandfather ] ──┐
[ Father's Paternal Grandmother ] ──┘                               │
                                                                    ├── [ Father ] ──┐
[ Father's Maternal Grandfather ] ──┐                               │                │
                                     ├── [ Paternal Grandmother ] ──┘                │
[ Father's Maternal Grandmother ] ──┘                                                ├── [ Selected User ]
                                                                                     │
[ Mother's Paternal Grandfather ] ──┐                                                │
                                     ├── [ Maternal Grandfather ] ──┐                │
[ Mother's Paternal Grandmother ] ──┘                               │                │
                                                                    ├── [ Mother ] ──┘
[ Mother's Maternal Grandfather ] ──┐                               │
                                     ├── [ Maternal Grandmother ] ──┘
[ Mother's Maternal Grandmother ] ──┘
```

Live implementation available at [shajjra.com Pedigree Explorer](https://shajjra.com).

### Model B: Interactive Canvas with CSS Tree Connectors
Using pure CSS pseudo-elements (`::before` and `::after`) to render tree branches dramatically reduces JavaScript overhead:

```css
/* Vertical and horizontal branching */
.tree ul ul::before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    border-left: 1px solid rgb(201 162 39 / 0.55);
    width: 0;
    height: 24px;
}
```

See the complete CSS implementation in [`assets/tree-modern.css`](../assets/tree-modern.css).

---

## 3. Zoom & Pan Navigation Engine

To allow seamless navigation across sprawling branches:
- **Transform Matrix:** Use CSS `transform: translate3d(x, y, 0) scale(z)` hardware acceleration.
- **Drag-to-Pan:** Listen to pointer events (`pointerdown`, `pointermove`, `pointerup`) with velocity damping.
- **Dynamic "Up to Father" Button:** A floating breadcrumb button that fetches the parent's coordinates and transitions the viewport smoothly.

Experience this directly on the [Live Interactive Tree](https://shajjra.com).

---
name: json-canvas
description: Create and edit JSON Canvas files (.canvas) with nodes, edges, groups, and connections. Use when working with .canvas files, creating visual canvases, mind maps, flowcharts, or when the user mentions Canvas files in Obsidian.
---

# JSON Canvas Skill

Create and edit `.canvas` files using the JSON Canvas spec (used by Obsidian Canvas and compatible apps).

## Overview

JSON Canvas is an open format for infinite canvas data. Files are JSON with `.canvas` extension.

## File Structure

```json
{
  "nodes": [...],
  "edges": [...]
}
```

## Nodes

Every node requires: `id`, `x`, `y`, `width`, `height`, `type`

### Generic Node Attributes

| Attribute | Type | Description |
|-----------|------|-------------|
| `id` | string | Unique identifier |
| `x` | number | X position (px) |
| `y` | number | Y position (px) |
| `width` | number | Width (px) |
| `height` | number | Height (px) |
| `color` | string | Optional color (preset or hex) |

### Text Nodes
```json
{"id": "a1", "type": "text", "text": "# Hello\nMarkdown supported", "x": 0, "y": 0, "width": 250, "height": 60}
```

### File Nodes
```json
{"id": "f1", "type": "file", "file": "Notes/My Note.md", "x": 300, "y": 0, "width": 250, "height": 60}
```

### Link Nodes
```json
{"id": "l1", "type": "link", "url": "https://obsidian.md", "x": 0, "y": 200, "width": 250, "height": 60}
```

### Group Nodes
```json
{"id": "g1", "type": "group", "label": "My Group", "x": -50, "y": -50, "width": 600, "height": 300}
```

## Edges

```json
{
  "id": "e1",
  "fromNode": "a1", "fromSide": "right",
  "toNode": "f1",   "toSide": "left",
  "label": "optional label",
  "color": "4"
}
```

**Side values:** `top`, `right`, `bottom`, `left`
**End shapes:** `none` (default), `arrow`

## Colors

| Value | Color |
|-------|-------|
| `"1"` | Red |
| `"2"` | Orange |
| `"3"` | Yellow |
| `"4"` | Green |
| `"5"` | Cyan |
| `"6"` | Purple |
| `"#RRGGBB"` | Custom hex |

## Layout Guidelines

- Default node size: 250 × 60 for text, 400 × 400 for files
- Spacing: 50–100px between nodes
- Groups: add 50px padding around contents

## ID Generation

Use short unique strings: `"a1"`, `"node-intro"`, `"step-3"`. Avoid UUIDs for readability.

## References

- Spec: https://jsoncanvas.org
- Obsidian docs: https://help.obsidian.md/canvas

# Puzzle Blueprint

**A visual dependency editor for designing adventure-game puzzles.**

Puzzle Blueprint helps writers and game designers map goals, puzzles, gates, items, clues, characters, locations, and world states as an interactive graph. Connect ideas with meaningful relationships, explore alternate solutions with AND/OR nodes, and export the finished blueprint for documentation or collaboration.

The entire app lives in a single HTML file. It has no build step, runtime dependencies, accounts, or backend.

## Features

- Ten purpose-built node types: Goal, Puzzle, Gate, Item, Clue, Character, Location, State, AND, and OR
- Six labeled relationships: Requires, Unlocks, Gives, Reveals, Uses, and Blocks
- Editable titles, design notes, node types, and progress statuses
- Drag-and-drop canvas with alignment guides, marquee selection, group movement, zooming, panning, and pinch gestures
- Automatic dependency layout and fit-to-screen controls
- Undo and redo history
- Browser autosave using `localStorage`
- Import and export of editable JSON graphs
- Presentation-ready SVG and high-resolution PNG exports
- Responsive desktop and touch-friendly mobile interface

## Try it locally

No installation or local server is required. Clone the repository:

```bash
git clone https://github.com/perezbalen/puzzle-blueprint.git
cd puzzle-blueprint
```

Then open `index.html` in any modern browser—for example, by double-clicking the file. Everything runs locally on your device.

## Quick start

1. Choose a node type from the left palette. The new node appears in the center of the canvas.
2. Select the node and use the inspector to edit its title, notes, type, and status.
3. Select a node's input or output pin, then select the opposite pin on another node.
4. Choose the relationship that describes the connection.
5. Arrange the graph manually or select **Auto Layout**.
6. Use **Save** to download an editable JSON file, or export the diagram as SVG or PNG.

Puzzle Blueprint starts with a sample graph based on the stone-disk entrance puzzle from *Indiana Jones and the Fate of Atlantis*, so you can explore the interaction model immediately. Select **New** when you are ready to begin from a blank canvas.

## Controls

| Action | Mouse and keyboard | Touch |
| --- | --- | --- |
| Select a node | Click | Tap |
| Select multiple nodes | Shift-click or drag on empty canvas | — |
| Move selected nodes | Drag a selected node's header | Drag a node's header |
| Pan | Hold Space and drag, or middle-drag | Drag empty canvas |
| Zoom | Mouse wheel or toolbar buttons | Pinch or toolbar buttons |
| Connect nodes | Select one pin, then the opposite pin | Tap one pin, then the opposite pin |
| Select all nodes | Ctrl/Cmd + A while the canvas is focused | — |
| Undo | Ctrl/Cmd + Z | Toolbar button |
| Redo | Ctrl/Cmd + Shift + Z or Ctrl/Cmd + Y | Toolbar button |
| Delete selection | Delete or Backspace | Inspector action |
| Cancel or clear selection | Escape | Tap empty canvas |

## Modeling a puzzle

Nodes represent the pieces of a puzzle, while directed connections explain how those pieces affect one another. For example:

```text
Enter the archive ──requires──▶ Door is unguarded
Door is unguarded ──requires──▶ Distract the librarian
Distract the librarian ──requires──▶ Any distraction works (OR)
```

Use **AND** when every connected dependency must be satisfied and **OR** when any one branch is sufficient. Node statuses—Working, Solved, and Blocked—make unresolved design work visible without changing the graph's logic.

## Saving and data ownership

The current graph, viewport, and panel preferences are saved automatically in the browser's local storage. Data stays on the device and no information is sent to a server.

Local browser storage is convenient but should not be your only backup. Use **Save** regularly to download the graph as JSON. A saved file includes the graph title, nodes, positions, statuses, notes, connections, and relationship types, and can be restored with **Load**.

## Project structure

```text
puzzle-blueprint/
├── index.html   # Markup, styles, editor logic, and sample graph
└── README.md
```

## Development

Puzzle Blueprint is built with plain HTML, CSS, and JavaScript. To contribute, edit `index.html`, refresh the browser, and test the affected desktop and touch interactions. There is currently no compilation or automated test step.

When changing the graph schema, preserve compatibility with existing JSON saves where possible. The current top-level format is:

```json
{
  "version": 1,
  "title": "My Puzzle Graph",
  "nodes": [],
  "edges": []
}
```

Contributions and bug reports are welcome through [GitHub Issues](https://github.com/perezbalen/puzzle-blueprint/issues).

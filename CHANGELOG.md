# Changelog

## v2.1.3 - 2026-11-09

Changes since v2.1.2 (published 2026-11-06).

### Added
- **Preset gallery.** The presets menu shows thumbnails generated locally on demand and cached in the browser. Thumbnails appear one by one as they are ready, including right after choosing a preset folder. Only Twister projects are listed when a preset folder is chosen (other JSON files are ignored).
- **Tangent handles in the profile editor.** Spline nodes show draggable in/out tangent handles. Handle lines keep their direction while panning and are clipped at the plot edge. Handle edits support undo/redo, and a node menu command resets a node's tangents to automatic.
- **Tangent handles on the CP splines ("Raio - CP").** With symmetry on, editing one CP's tangent is replicated to the CPs aligned with it in the symmetry group; with symmetry off, only that CP changes.
- **Independent / Linked tangents selector** for each spline node. The link lasts for the session only and is not saved in the project file.
- **Pan and zoom in both 2D editors.** The wheel zooms around the cursor, dragging the background pans, and a Frame button resets the view. Each project tab keeps its own view. Vertical pan follows the drag direction, a pan that starts on the background stays a pan over handles, and the insert-node dialog suggests the height and radius of the clicked point under the current zoom. The Z line moves only when dragged over the line itself.
- **Fine node heights.** Nodes can be inserted at close heights (for example 0.15 mm between 0.10 and 0.20) with "Insert node with values...". Inserting at an occupied height shows a warning and replaces nothing. Overlapping nodes can be chosen from a "Choose node" list.
- **Ten built-in presets:** eight author-supplied presets plus two distinct earlier models (duplicate contents are not repeated).

### Fixed
- The About dialog showed version 2.1.1; it now shows the same version as the title, badge and saved projects.

### Notes and limits
- Project files that contain CP tangents are saved as project format 2. Earlier releases (v2.1.2 and older) refuse to open them. Files without CP tangents keep format 1. Save test projects as new files instead of overwriting originals.
- Touch gestures were checked with emulation. Testing on a physical tablet is planned for a later release.
- Three.js r128 and the single-file `index.html` setup are unchanged.

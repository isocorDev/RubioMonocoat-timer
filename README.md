# RubioMonocoat-timer

This tool makes it easy to keep track of timing when using Rubio Monocoat on woodworking projects.

**Open the app:** [isocordev.github.io/RubioMonocoat-timer](https://isocordev.github.io/RubioMonocoat-timer/)

It's a static page with no build step, meant to run on GitHub Pages from a phone in the shop. Everything runs in your browser and is saved there; nothing is uploaded.

## Plan, before the gloves go on

1. **Load your parts.** Choose a STEP file exported from Fusion 360. Each component becomes a part with its name, size, and real surface area. Hinges, screws, and tiny parts are set to Skip. You can also type a list, or skip planning and use the timer on its own.
2. **Choose how each part gets finished.** Pick 2 faces (face 1, then flip for face 2), 1 face, Whole (one timer), or Skip. Rename parts, reorder them, or check several and Combine them into one piece, like an assembled case.
   - **3D view.** STEP parts appear in 3D with face 1 in orange and face 2 in blue. Face 1 starts as the least visible side: undersides of horizontal panels, and inside faces of everything else.
   - **Selecting on a phone.** Tap a part to select it, and the rest of the model turns see-through so nothing blocks it. Tap one of its broad faces to make that face 1. The arrows step through parts one by one and frame each part's face 1, so you rarely need to orbit by hand.
   - **Navigation when you want it.** Drag to orbit, pinch to zoom, two fingers to pan, double tap to zoom to a part. Front, Top, Side, and 3/4 presets, an Explode slider for interior parts, Hide, Upright (if the model loads on its side), and Full screen.
3. **How much to mix.** Gives ml and grams of Part A and Part B, how long applying will take, and splits the job into batches if it runs past pot life.

Try it with [`samples/sample-bookshelf.step`](samples/sample-bookshelf.step), or tap **Load sample bookshelf**.

## Finish, with gloves on

- **One big Next button** always does the most urgent thing: wipe the oldest ready surface, mark a bleed-back pass checked, or apply the next planned surface. When nothing is due it says what it's waiting for.
- **Undo** reverses the last tap.
- **Compact list.** Every wet and watched surface is one row, sorted by when it needs you, with a countdown and its own button. Up next shows the rest of the plan.
- **Part icons.** Each row shows a small render of the part with the face you're on highlighted. Tap the row to expand it: a bigger picture, size, area, wipe window, wipe time, checks, and a Show in 3D link.
- **Spoken alerts** say what to do ("Wipe Shelf 1, face 1").
- **No-touch control.** A Bluetooth keyboard or page-turner foot pedal works: Space, Enter, Page Down, or Right arrow for Next, and Page Up, Left arrow, or Backspace for Undo. Voice control listens for "next", "wiped", "checked", "apply", and "undo" in Chrome, Edge, and Safari.
- **Batch pot life**, with a suggested amount for the next batch.
- **Leaving checklist:** rags, heater, cans capped, last flashlight pass.

Without a plan, Next starts unnamed timers (Surface 1, Surface 2, and so on), which is how the first version worked.

## Default timings and where they come from

| Setting | Default | Basis |
| --- | --- | --- |
| Sit before wiping | 15 min | Rubio US floor instructions (2024): react at least 5 min, start removing around 15 min. The data sheet says "a few minutes." |
| Wipe deadline | 30 min | Rubio Oil Plus 2C data sheet: remove all excess within 30 min max. |
| Bleed-back check | every 30 min for 4 h | Shop practice for open-grain wood like red oak. Not a Rubio spec. |
| Pot life | 4 h warning, 6 h limit | Data sheet: use within 4 to 6 hours of mixing. |
| Coverage | 300 sq ft/L, +15% | Rubio rates 300 to 500 sq ft/L; open grain sits at the low end. |
| Wet at once | 3 | How many surfaces you work before wiping. |

Warm, dry air (a space heater, for example) shortens the working window. If the oil feels tacky when you wipe, lower the sit time. Every value is adjustable under Settings.

## STEP reading

STEP files are read in the browser with [occt-import-js](https://github.com/kovacsv/occt-import-js) (OpenCascade compiled to WebAssembly), vendored in `vendor/` with its licenses. The 7.6 MB reader only loads when you choose a file. If it can't load, the app falls back to reading part names from the file's text, and you enter areas by hand.

The 3D view and icons use [three.js](https://threejs.org) r128 from cdnjs. Part shapes are kept in the browser's IndexedDB, so the 3D view and icons come back after a reload without reading the STEP file again.

## Hosting

Settings → Pages → Deploy from a branch → `main` / root.

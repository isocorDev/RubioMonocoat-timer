# RubioMonocoat-timer

This tool makes it easy to keep track of timing when using Rubio Monocoat on woodworking projects.

**Open the app:** [isocordev.github.io/RubioMonocoat-timer](https://isocordev.github.io/RubioMonocoat-timer/)

## What it does

- **Surface timers.** Name a surface and tap Applied. Each card counts down the sit time, then the wipe window, then switches to bleed-back checks after you tap Wiped. Add as many as you need; cards sort by urgency.
- **Batch pot life.** Tap Mixed a batch when A and B are combined. It warns at 4 h and marks the batch spent at 6 h.
- **How much to mix.** Enter how long you'll be applying and your average surface size. It estimates surfaces, area, and ml of Part A and Part B (3:1).
- **Leaving checklist.** Rags, heater, cans capped, last flashlight pass.

Alerts beep, vibrate where supported, and show browser notifications if you turn them on. State is saved in the browser, so a reload keeps your timers.

## Default timings and where they come from

| Setting | Default | Basis |
| --- | --- | --- |
| Sit before wiping | 15 min | Rubio US floor instructions (2024): react at least 5 min, start removing around 15 min. The data sheet says "a few minutes." |
| Wipe deadline | 30 min | Rubio Oil Plus 2C data sheet: remove all excess within 30 min max. |
| Bleed-back check | every 30 min for 4 h | Shop practice for open-grain wood like red oak. Not a Rubio spec. |
| Pot life | 4 h warning, 6 h limit | Data sheet: use within 4 to 6 hours of mixing. |
| Coverage | 300 sq ft/L, +15% | Rubio rates 300 to 500 sq ft/L; open grain sits at the low end. |

Warm, dry air (a space heater, for example) shortens the working window. If the oil feels tacky when you wipe, lower the sit time. Every value is adjustable under Settings.

## Hosting

Settings → Pages → Deploy from a branch → `main` / root.

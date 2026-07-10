# Dynamic Lane Reconfiguration for Ambulance Priority

A software simulation of a smart traffic management system that gives ambulances
priority access at intersections by dynamically overriding signal timing and
reconfiguring lane access — reimplemented from an original **Tinkercad/Arduino
embedded systems prototype** as a browser-based simulation.

**[Live Demo →](#)** *(add your GitHub Pages link here once deployed)*

![status](https://img.shields.io/badge/status-active-brightgreen)
![license](https://img.shields.io/badge/license-MIT-blue)

---

## Overview

The original project used IR/ultrasonic sensors and an Arduino to detect an
approaching ambulance and override standard traffic signal timing. This
repository re-implements the same control logic entirely in software — a
finite-state controller written in vanilla JavaScript drives an SVG
intersection, so the system can be run, tested, and demonstrated with nothing
but a browser.

| Original hardware component | Software equivalent here |
|---|---|
| IR / ultrasonic sensor | Simulated detection event (button trigger) |
| Arduino control logic | JavaScript finite-state machine |
| Traffic signal LEDs | Animated SVG signal states |
| Servo-actuated lane gates | Dynamic lane-gate open/close logic |
| Serial monitor output | Live system log panel |

## Features

- **Normal traffic cycle** — alternating N/S and E/W green phases on a timer
- **Priority override** — an ambulance event on any approach immediately
  forces that direction to green and all others to red
- **Dynamic lane reconfiguration** — a reserved lane opens on the priority
  approach and closes automatically once the ambulance clears
- **Live system log** — every sensor event, signal change, and lane action is
  timestamped and streamed to an on-screen log, mirroring an embedded
  system's serial monitor output
- **Response-time readout** — measures and displays how quickly the
  intersection clears under priority mode

## Tech stack

Pure HTML, CSS, and JavaScript — no build step, no dependencies, no backend.
This keeps the project trivially deployable (GitHub Pages, Netlify, Vercel,
or just opening `index.html` locally) and easy for anyone reviewing your
portfolio to run instantly.

## Running locally

```bash
git clone https://github.com/<your-username>/ambulance-priority-system.git
cd ambulance-priority-system
open index.html   # or just double-click the file
```

No installation required.

## Project background

This started as a hardware prototype built in Tinkercad, using simulated
sensors and an Arduino to demonstrate ambulance-priority traffic control as
an embedded systems concept. This repository translates that same control
logic — detection, override decision, signal change, lane reconfiguration —
into a standalone software simulation, so the underlying algorithm can be
explored, tested, and extended without any physical hardware.

## Possible extensions

- Multiple simultaneous ambulance requests with a priority queue
- Adjustable simulated traffic density per approach
- A Python/Node backend exposing the controller logic as an API
- Integration with a mapping API to simulate real GPS-based detection
- Unit tests for the state machine logic

## Contributors

- **E. Sankar** — project design & implementation
- **[VANJI MUTHU P](https://github.com/muhilvanji987-lang)** — collaborator

## License

MIT — see [LICENSE](LICENSE).

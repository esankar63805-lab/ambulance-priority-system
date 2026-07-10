# Dynamic Lane Reconfiguration for Ambulance Priority
### Smart Traffic Management System — Portfolio Case Study

**Developed by:** E. Sankar
**Collaborator:** Vanji Muthu P — [github.com/muhilvanji987-lang](https://github.com/muhilvanji987-lang)
**Category:** Embedded Systems → Software Engineering / Intelligent Transportation
**Tech stack:** JavaScript, HTML5, SVG, CSS3 (originally prototyped in Tinkercad/Arduino)
**Live demo:** *add your GitHub Pages link here after deployment*
**Source code:** *add your GitHub repo link here*

---

## 1. Project Summary

This project is a smart traffic management system that gives ambulances
priority access at road intersections by dynamically controlling traffic
signals and reconfiguring lane access in real time. It began as an embedded
systems prototype built in Tinkercad, and was later re-engineered as a
standalone software simulation — a browser-based system driven by a
JavaScript finite-state controller — so the underlying control logic can be
run, demonstrated, and extended without any physical hardware.

The system models a real-world problem: emergency vehicles are frequently
delayed at signal-controlled intersections, which directly increases
emergency response time. This project demonstrates one way that embedded
sensing and intelligent signal control can address that problem, and how
the same control logic translates cleanly into a pure-software
implementation.

## 2. Problem Statement

Every second an ambulance spends waiting at a red light is a second lost in
a medical emergency. Traditional traffic signals run on fixed timers and
have no awareness of emergency vehicles approaching. This leads to:

- Increased ambulance response time
- Unnecessary risk from ambulances running red lights to save time
- No standardized way for emergency vehicles to communicate intent to the
  traffic infrastructure

## 3. Objective

Design a system that:
1. **Detects** an approaching ambulance at any of the four approaches to an
   intersection
2. **Overrides** the normal signal cycle to immediately grant that approach
   a green signal
3. **Reconfigures lane access** dynamically to give the ambulance a clear,
   dedicated path
4. **Reverts automatically** to the normal traffic cycle once the ambulance
   has passed through

## 4. Original Hardware Prototype (Tinkercad)

The original build used simulated embedded hardware to demonstrate the
concept:

| Component | Role |
|---|---|
| IR / ultrasonic sensors | Detect an approaching ambulance at each approach |
| Arduino microcontroller | Runs the decision logic and controls outputs |
| Traffic signal LEDs | Represent the red/amber/green states per approach |
| Servo motors | Simulate physical lane gates/barriers opening and closing |
| Serial monitor | Logs each detection and control decision |

## 5. Software Re-Implementation

To make the project accessible as a portfolio piece — runnable by anyone,
instantly, in a browser — the same control logic was rebuilt entirely in
software:

| Hardware concept | Software equivalent |
|---|---|
| IR/ultrasonic sensor trigger | Simulated detection event (UI button) |
| Arduino decision logic | JavaScript finite-state machine |
| Traffic signal LEDs | Animated SVG signal states |
| Servo-actuated lane gate | Dynamic SVG lane-gate open/close logic |
| Serial monitor output | Live, timestamped system log panel in the UI |

No servers, frameworks, or build tools are required — the entire simulation
runs client-side from a single HTML file, which makes it trivial to deploy
(GitHub Pages) and trivial for a recruiter or reviewer to try out.

## 6. System Architecture

```
 ┌────────────────────┐        ┌────────────────────────┐
 │  Detection Layer    │  --->  │   Priority Controller    │
 │ (sensor event / UI)  │        │  (finite-state machine)  │
 └────────────────────┘        └────────────┬───────────┘
                                             │
                     ┌───────────────────────┼───────────────────────┐
                     ▼                       ▼                       ▼
           ┌─────────────────┐    ┌──────────────────┐    ┌──────────────────┐
           │ Signal Control    │    │ Lane Gate Control  │    │  System Log        │
           │ (N/S/E/W states)  │    │ (open/close gates)  │    │ (event stream)      │
           └─────────────────┘    └──────────────────┘    └──────────────────┘
```

**Control flow:**
1. Normal cycle alternates N/S and E/W green phases on a fixed timer.
2. A detection event on any approach immediately halts the normal cycle.
3. The controller sets that approach to green and all others to red.
4. The corresponding lane gate opens, giving the ambulance a clear path.
5. Once the ambulance clears the intersection, the gate closes and the
   normal cycle resumes.
6. Every step is logged with a timestamp, mirroring the serial monitor
   output of the original embedded version.

## 7. Key Features

- **Real-time signal override** on ambulance detection from any of 4
  approaches
- **Dynamic lane reconfiguration** — a dedicated lane opens only when
  needed and closes automatically afterward
- **Live system log** — timestamped event stream showing every sensor
  trigger, signal change, and lane action
- **Response-time measurement** — the system measures and displays how
  quickly the ambulance clears the intersection under priority mode
- **Zero-dependency deployment** — runs anywhere a browser runs, with no
  installation

## 8. My Role (E. Sankar)

- Designed the original ambulance-priority concept and control logic
- Built the initial hardware prototype and circuit logic in Tinkercad
- Led the redesign of the system as a standalone software simulation
- Implemented the finite-state signal controller and lane-reconfiguration
  logic in JavaScript
- Designed the intersection visualization and system log UI
- Wrote project documentation and prepared the project for GitHub/portfolio
  presentation

*(Vanji Muthu P collaborated on the original project — see repository for
full contributor credit.)*

## 9. Skills Demonstrated

- Embedded systems design and sensor-driven logic (Tinkercad/Arduino)
- Finite-state machine design
- Translating hardware control logic into software architecture
- Front-end development: HTML5, CSS3, SVG animation, vanilla JavaScript
- UI/UX for real-time systems and live data/log visualization
- Git/GitHub workflow and static site deployment (GitHub Pages)
- Technical documentation and project presentation

## 10. Impact / Outcome

While this is a simulation rather than a deployed traffic system, it
demonstrates a complete, working model of the core problem: reducing
emergency vehicle response time through automated, sensor-driven priority
control — a technique used in real-world intelligent transportation
systems. It also demonstrates the ability to take a concept from embedded
hardware prototyping through to a polished, shareable software artifact.

## 11. Future Improvements

- Priority queueing for multiple simultaneous ambulance requests from
  different approaches
- Adjustable simulated traffic density to model congestion effects
- A backend service (Node/Python) exposing the controller as an API for
  integration with real sensor data or a mapping/GPS service
- Automated tests for the state-machine logic
- Migration to a component framework (React) for a larger-scale version

---

*This document is intended for inclusion in a personal portfolio site,
resume project section, or GitHub repository. Update the live demo and
source code links once deployed.*

# Solar-System-simulation

![Simulation Screenshot](sample.jpg)

A minimal, browser-based N-body demo where particles orbit a central star, collide, and form planets and moonlets. Witness gravity at work in real time!

**Live Demo:**  
https://shahryarfp.github.io/Solar-System-simulation/

---

## Overview

This interactive simulation recreates a tiny “solar system” in your browser. At its heart is a single massive star surrounded by hundreds of smaller bodies. As you watch:

- Particles swirl and settle into orbit around the star.
- Close encounters and gentle collisions allow particles to stick together and grow into planet-like bodies.
- Some bodies develop small moonlets that trace their own faint paths.
- Rare, head-on collisions with the star create bright “explosions” of debris.

It’s a dynamic dance of gravity, motion, and merging that plays out in vivid color.

---

## Core Physical Rules

While the simulation runs entirely in JavaScript, it models three main ideas from classical mechanics:

1. **Mutual Attraction**  
   Every body pulls on every other body.  
   - The strength of the pull depends on how massive each object is, and how far apart they are.  
   - More massive bodies (like the central star) exert a stronger pull on their smaller companions.

2. **Orbiting Motion**  
   Once a body is in motion around the star, its path curves into an orbit.  
   - Bodies moving faster or closer to the star go around more quickly.  
   - Distant or slower bodies take longer, tracing wide, graceful loops.

3. **Collisions and Merging**  
   When two bodies bump gently into each other, they’ll merge into one larger object:  
   - The new body carries on with the combined mass and an averaged velocity, preserving the overall momentum.  
   - If two bodies slam together too hard or one crashes into the star, you’ll see a quick “explosion” effect as debris flies outward.

Over time, these simple rules let the system self-organize into a collection of planets and moonlets, each with its own unique orbit.

---

## Key Features

- **Real-Time N-Body Dynamics**  
  Watch up to a thousand particles interact under gravity.

- **Trace Paths**  
  Each planet leaves a fading trail so you can follow its orbit.

- **Moonlet Detection**  
  Smaller bodies that complete full circuits around larger ones become highlighted as moon companions.

- **Collision Effects**  
  Soft merges grow planets; hard crashes into the star produce colorful debris bursts.

- **Adjustable Parameters**  
  Tweak particle count, gravitational strength, time-step size, and speed factor via the on-screen controls.  

---

## How to Run

1. Clone or download this repository.
2. Open `index.html` in any modern web browser.
3. Use the **Show Controls** button to reveal sliders and input fields.
4. Adjust settings to your taste, then click **Reset** to restart the simulation with your new parameters.

---

## Available Controls

- **Initial Particles**: Number of small bodies to start with (50–1000).  
- **Speed Factor**: Scales the initial orbital speeds.  
- **G (Gravity Strength)**: Overall strength of the gravitational pull.  
- **dt (Time Step)**: How finely the simulation slices time. Smaller values give smoother motion at the cost of performance.  

# Solar-System-Simulation

![Simulation Screenshot](sample.jpg)

A minimal, browser-based N-body demo where particles orbit a central star, collide, and accrete into planets and moonlets. Watch as orbits form, bodies merge under gravity, and “explosions” mark destructive sun-planet collisions.

**Live Demo:**  
https://shahryarfp.github.io/Solar-System-simulation/

---

## 🚀 Features

- **Realistic gravity**: All bodies attract one another via the inverse-square law.
- **Symplectic integration**: A leapfrog scheme for stable, time-reversible orbits.
- **Collision & merger**: Small bodies coalesce into larger ones when they approach below a threshold.
- **Sun impacts**: Planets that collide with the star generate visual “explosions” effects.
- **Moonlet detection**: Bodies that complete two full orbits around a planet become tracked as moons.
- **Interactive controls**: Tweak particle count, gravitational constant, timestep, and more.
- **Dynamic spawning**: Maintains a minimum number of planets by spawning new ones at the boundary.

---

## 🌌 How It Works

### 1. Gravity & Motion

Each pair of bodies *i* and *j* exerts a mutual force  
\[
F = G \,\frac{m_i\,m_j}{r^2_\text{eff}}
\]
where  
- **G** is the universal gravitational constant (tunable in UI),  
- \(r_\text{eff} = r + \Delta\) for star–planet pairs (offset \(\Delta\) prevents numerical “singularity” at the sun’s surface),  
- \(m_i, m_j\) are the masses,  
- and \(r\) is the center-to-center distance.

Accelerations are \(\displaystyle \mathbf{a}_i = \sum_j \frac{\mathbf{F}_{ij}}{m_i}\).

### 2. Numerical Integration

We use a **leapfrog integrator** (a symplectic, second-order method) to update velocities and positions:
1. Half-step velocity update:  
   \(\displaystyle \mathbf{v}\bigl(t + \tfrac{\Delta t}{2}\bigr) = \mathbf{v}(t) + \tfrac{\Delta t}{2}\,\mathbf{a}(t)\)
2. Full-step position update:  
   \(\displaystyle \mathbf{x}(t + \Delta t) = \mathbf{x}(t) + \Delta t\,\mathbf{v}\bigl(t + \tfrac{\Delta t}{2}\bigr)\)
3. Recompute accelerations at \(t + \Delta t\)
4. Complete velocity update to \(t + \Delta t\)

This preserves energy and angular momentum much better than Euler’s method.

### 3. Collision & Merging

- **Planet–planet mergers** occur when two bodies approach within  
  \(\displaystyle R_i + R_j\;\times\;\text{mergeDistFactor}\)  
  *and* their relative speed is below a threshold.  
- **Inelastic**: Merged bodies conserve total mass and momentum, and radius is recomputed assuming constant density.
- **Sun impacts**: Any planet intersecting the sun’s radius triggers an “explosion” animation (no remnant planet).

### 4. Moon Detection

A small body becomes a **moonlet** if:
1. It orbits a larger planet within its Hill sphere  
   \(\displaystyle R_H = a \bigl(\tfrac{m_\text{planet}}{3\,m_\text{star}}\bigr)^{1/3}\)
2. It accumulates at least two full revolutions (tracked via accumulated angular change).

Traces for moons are drawn with dashed lines.

---

## ⚙️ Controls & Parameters

Use the **Show Controls** button to open the settings panel:

| Control                | Description                                                                           |
|------------------------|---------------------------------------------------------------------------------------|
| **Initial Particles**  | Number of small bodies to spawn around the star at reset (50–1000).                  |
| **Speed Factor**       | Scales orbital velocities relative to circular speed.                                 |
| **G (Universal)**      | Gravitational constant; higher ⇒ stronger attraction, more violent dynamics.         |
| **dt (Timestep)**      | Integration timestep; smaller ⇒ more accurate but slower simulation.                  |

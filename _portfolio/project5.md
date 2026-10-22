---
title: Thermal Expansion of a Rotary Vane Pump
subtitle: A COMSOL simulation of how a pump housing grows when pumping 140°F glue.
image: assets/img/portfolio/05-Stress.png
alt: COMSOL displacement plot of the rotary vane pump housing

caption:
  title: Thermal Expansion
  subtitle: COMSOL Simulation
  thumbnail: assets/img/portfolio/05-Displacement.png
---
<style>
.project-figure {
  text-align: center;
}
.portfolio-modal .modal-content .project-figure img {
  display: block;
  margin: 0 auto 0.4em auto;
  max-width: 100%;
  height: auto;
}
.portfolio-modal .modal-content .project-figure figcaption {
  font-size: 0.9em;
  color: #6c757d;
  font-style: italic;
  margin-top: 0;
}
.portfolio-modal .modal-content ul {
  text-align: left;
  display: inline-block;
}
.portfolio-modal .modal-content .video-wrapper {
  width: 100%;
  aspect-ratio: 16 / 9;
  margin: 0 auto 0.4em auto;
}
.portfolio-modal .modal-content .video-wrapper iframe {
  width: 100%;
  height: 100%;
}
</style>

**Overview**

Simulation of Physical Processes (ME526) covered numerical methods for solving nonlinear partial differential equations and the fundamentals of the finite element method, using MATLAB and COMSOL Multiphysics to model problems across structural mechanics, materials science, aerospace, and physics. The course ended with a project where teams of three chose something to simulate.

At the time, one of my teammates, Jos, was also taking ME559, where his team was designing a rotary vane pump to move heated PVA glue at 140°F in a factory. A pump housing that grows from heat could change the fit between the housing and the rotor and vanes, so we simulated how much the professor's gray iron housing would expand going from room temperature (70°F) to the 140°F operating temperature.

**My Role**

I built the model's geometry, set up the constraints and boundary conditions, and ran the simulations, working alongside Jos on one computer while we learned COMSOL together. I also helped write the step-by-step instructions in our report for recreating the simulation.

**Model Setup**

Because the professor's housing has a simple profile, a 2D model was enough for this estimate. The geometry is a ring with a 3.6" inner diameter and 4.7" outer diameter, sitting on a rectangular base.

- **Physics:** Heat Transfer in Solids coupled with Solid Mechanics, solved as a stationary (steady-state) study.
- **Material:** Gray iron, modeled with COMSOL's built-in cast iron and adjusted by hand to match published data for ASTM A48 Class 40 gray iron (thermal expansion coefficient 11 × 10⁻⁶ 1/K, Young's modulus 140 GPa, Poisson's ratio 0.25).
- **Structural boundary:** The bottom of the base is fixed, like a pump bolted down in a factory. Every other edge is free to move.
- **Thermal boundaries:** The inner bore is held at the glue's 140°F. The outer surfaces are insulated, since the pump sits in still air and loses very little heat to its surroundings. This makes the result a worst case, where the whole housing reaches the glue's temperature.
- **Mesh:** Extra fine.

<figure class="project-figure">
  <img src="assets/img/portfolio/05-Geometry.png" alt="2D geometry of the pump housing and base">
  <figcaption>The simplified 2D geometry of the housing and base.</figcaption>
</figure>

**Results**

With the outer surfaces insulated, the housing settles at a uniform 140°F. Because the base is fixed, the housing can only grow upward and outward, so the largest displacement, about 0.003", is at the top of the ring, farthest from the base. The highest stresses are at the corners of the base, away from the parts of the housing that matter for the pump's operation.

<figure class="project-figure">
  <img src="assets/img/portfolio/05-Displacement.png" alt="Displacement plot of the housing">
  <figcaption>Displacement from thermal expansion, greatest at the top of the housing, farthest from the fixed base (deformation exaggerated).</figcaption>
</figure>

**Checking the Simulation by Hand**

To make sure the results were reasonable, we compared them with linear thermal expansion calculated by hand, D<sub>new</sub> = D × (1 + α × ΔT), using ΔT = 70°F and α = 6.11 × 10⁻⁶ 1/°F (the same 11 × 10⁻⁶ 1/K used in the simulation):
 
- **Inner diameter:** 3.6 × (1 + 6.11 × 10⁻⁶ × 70) = 3.60154", an increase of about 0.0015".
- **Outer diameter:** 4.7 × (1 + 6.11 × 10⁻⁶ × 70) = 4.70201", an increase of about 0.0020".
 
Since the base is fixed, the bottom of the ring can't move, so the top moves by the full change in diameter rather than the change in radius. That's why we compared the simulation against the change in diameter, and the two gave similar values.

**Challenges**

- **Units:** COMSOL read our temperatures in °F as kelvin, even when the units were written into the parameters. Entering 140°F that way produced compression instead of expansion and results that were off by orders of magnitude. Converting every temperature to kelvin fixed it.
- **Solver tolerance:** COMSOL's default relative tolerance didn't work with our mesh size, so we had to either set the mesh size manually, finer than COMSOL's built-in options, or adjust the solver's relative tolerance.
- **How much to simplify:** We first considered a 3D model and spent time deciding how much we could simplify the geometry while still getting a useful answer. The 2D model turned out to be enough.

**Conclusion**

The housing's bore grows by only about 0.0015" at 140°F. In a rotary vane pump, the vanes slide outward from centrifugal force as the rotor spins, so they stay in contact with the housing wall and take up that small change on their own. Thermal expansion of the housing isn't significant enough to account for in this pump's design.

The same approach applies to other parts that run hot, such as pumps for other fluids, turbine and turbocharger housings, and rotary (Wankel) engines. I'm now building this same pump design in ME559 (see the Rotary Vane Pump project).

Want to see the full report, including step-by-step modeling instructions? [Read it here.](/assets/files/03-COMSOL_Report.pdf){:target="_blank"}

- September 2025 - December 2025
- Simulation of Physical Processes - ME526

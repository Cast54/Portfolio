---
title: Rotary Vane Pump
subtitle: Building a rotary vane pump to tighter-than-drawing tolerances, then redesigning it to pump liquid ammonia.
image: assets/img/portfolio/04-Casting.jpg
alt: Rotary vane pump components

caption:
  title: Rotary Vane Pump
  subtitle: A Work in Progress
  thumbnail: assets/img/portfolio/04-Housing.jpg
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

Manufacturing Processes for Design and Production is a BU course built around the rotary vane pump. It teaches how a product's function, materials, and manufacturing methods all shape its cost, quality, and schedule, covering material selection, GD&T, metrology, design for manufacturing and assembly, and production costing. The course has two halves: first, every student builds a pre-designed pump from scratch; then, teams redesign that pump for a specific fluid and application. This project is still in progress, so this page covers what I've built so far.

**Building the Pump**

The build uses a range of processes, including sand casting, CNC and manual milling, turning, drilling and tapping, and laser cutting. We started by sand casting the bearing holders, then turned the steel shaft that drives the pump. Since I came into the course with more machining experience than most students, I challenged myself to hold my parts to ±0.001" where the drawings only called for ±0.005".

<figure class="project-figure">
  <img src="assets/img/portfolio/04-Shaft.jpg" alt="Turned steel pump shaft">
  <figcaption>The turned steel shaft, held to ±0.001".</figcaption>
</figure>

Next came the pump housing. The overall shape was precut, so we sized the center bore that forms the pump's internal chamber on the lathe (I used a CNC lathe), then drilled and tapped the inlet and outlet ports with 1/4" NPT threads.

<figure class="project-figure">
  <img src="assets/img/portfolio/04-Housing_Holes.jpg" alt="Pump housing">
  <figcaption>The pump housing with its bored chamber and 1/4" NPT ports.</figcaption>
</figure>

**The Rotor Bore**

Then we started on the rotor, which holds the pump's vanes. So far, I've drilled the center hole and turned the rotor to thickness; the outer diameter and the vane slots are still to come.

The center hole had the tightest tolerance in the build: 0.7480" +0.0005/−0.0000. Most students drilled close to size and finished with a reamer from the tailstock. I didn't trust that approach, because the lathes' tailstocks aren't aligned with the spindle's axis of rotation, so a reamer would follow that misalignment. Instead, I bored the hole with a boring bar, which cuts true to the spindle.

That raised a new problem: there was no way to measure a hole to that tolerance. The best tool available was calipers, which are only good to about ±0.001". Outer diameters, though, can be measured precisely with micrometers, so I machined my own stepped plug gauge out of aluminum. One step measured 0.74805" and the other 0.7481". If the smaller step slid into the bore but the larger one didn't, the hole had to be between 0.74805" and 0.7481", safely inside the 0.7480–0.7485" tolerance.

<figure class="project-figure">
  <img src="assets/img/portfolio/04-Unfinished_Rotor.jpg" alt="Rotor with bored center hole">
  <figcaption>The rotor with its bored center hole.</figcaption>
</figure>

The tolerance mattered because the 0.750" shaft is shrink fit into this bore, so a hole that was too large would leave the rotor loose, and one too small wouldn't go together. With my bored hole, the shaft fit.

<figure class="project-figure">
  <img src="assets/img/portfolio/04-Shrink_Fit.jpg" alt="Rotor shrink fit onto the shaft">
  <figcaption>The rotor shrink fit onto the shaft.</figcaption>
</figure>

**Redesigning for Liquid Ammonia**

The pump we're all building is intentionally poorly designed, and the second half of the course is about doing better. Each team of three is assigned a fluid and application and has to redesign the pump around it, considering temperature, inlet and outlet pressure, speed, required lifespan, where it's installed, yearly production volume, and the fluid itself, which can be highly corrosive.

My team is designing a pump for liquid ammonia, with these requirements:

- **Temperature:** −50°F
- **Inlet pressure:** 1 atm
- **Outlet pressure:** 8 atm
- **Speed:** 3,600 RPM
- **Mean time between failures:** 4,500 hours of continuous operation
- **Installation:** Manufacturing facility
- **Production volume:** 250 units per year

**Next Steps**

We've just started the redesign. By the end of the course, we'll produce fully dimensioned drawings with GD&T for every component, plus assembly drawings, all detailed enough to send to a real manufacturer. (The redesigned pumps won't be built in the course.) I'll keep updating this page as the build and redesign progress.

{:.list-inline}
- September 2026 - Present
- Manufacturing Processes for Design and Production - ME559

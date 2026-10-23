---
title: Dynamic Gas System
subtitle: Upgrading the lab's carbon capture test rig with new sample holders and a 3D-printed cooling funnel.
image: assets/img/portfolio/06-DGS_After.jpg
alt: The Dynamic Gas System with the new air funnel installed

caption:
  title: Dynamic Gas System
  subtitle: Carbon Capture Test Rig Upgrades
  thumbnail: assets/img/portfolio/06-DGS_Thumbnail.jpg
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

The Lubner Group at BU works on direct air capture (DAC), pulling CO₂ directly out of the air. A big part of that work is testing sorbents (materials that capture CO₂), such as metal-organic frameworks (MOFs), which are highly porous. The lab tests them on the Dynamic Gas System (DGS), a benchtop rig that cycles a sample through capturing and releasing CO₂ while measuring how much it takes in.

I didn't build the DGS, but since joining the lab in May 2026 I've been working on making it faster and more flexible: new sample holders, a faster cooling system, a test of a faster-heating tube, and tests of larger tubes. I also built the DAC Vacuum Chamber (see its own project page), which can replace the DGS's tube furnace for samples that need a true vacuum or don't fit in the tube.

**The System**

The DGS is made up of:

- **Two Alicat MC mass flow controllers** (up to 500 SCCM, standard cubic centimeters per minute): one for CO₂ and one for nitrogen, joined by a tee.
- **A gas humidifier** to add water vapor to the gas stream.
- **A tube furnace:** a 200 mm long copper tube (1/4" OD) wrapped in nichrome heating wire, with a layer of Kapton tape between the wire and the tube and another layer over the wire. The copper tube sits inside a glass tube with a 46 mm bore.
- **A LI-COR LI-850 gas analyzer** that measures CO₂ and water vapor at the outlet.
- **A BK Precision 9129B programmable power supply** that powers the heater and the cooling fan.
- **A laptop running the DGS Control Center**, the lab's custom software that controls everything and logs the data.

Samples sit in small aluminum holders inside the copper tube. Flexible tubing connects one end of the tube to the flow controllers and the other end to the gas analyzer.

**Recipes**

The software runs "recipes," sequences of steps that each set the gas, flow rate, duration, temperature, and fan. One cycle might look like this:

- **Purge:** 200 SCCM N₂, 5 min, room temperature (RT), fan off. Flushes the system with pure nitrogen.
- **Calibrate:** 100 SCCM N₂, 2 min, RT, fan off. Calibrates the CO₂ analyzer.
- **Adsorb:** 200 SCCM CO₂, 10 min, RT, fan off. The sorbent captures CO₂.
- **Purge:** 200 SCCM N₂, 5 min, RT, fan off. Clears leftover CO₂ from the lines, so the next step only measures what the sorbent releases.
- **Desorb:** 200 SCCM N₂, 5 min, 160°C, fan off. Heat drives the captured CO₂ back out of the sorbent.
- **Cool:** 200 SCCM N₂, 5 min, RT, fan on. Cools the system back down.

The tube can't pull a vacuum, so desorption happens under flowing nitrogen instead. Pure nitrogen keeps the CO₂ concentration around the sample near zero, which drives CO₂ out of the sorbent the way a vacuum would. Throughout the recipe, the software logs the tube temperature and the CO₂ and water vapor concentrations, which is how the lab measures how much CO₂ a sample captured and released. Long-duration tests repeat cycles like this many times.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-DGS_Control_Center.jpg" alt="Laptop running the DGS Control Center software">
  <figcaption>The DGS Control Center, which runs the recipes and logs the data.</figcaption>
</figure>

**New Sample Holders**

The original sample holders were thin aluminum sheets bent into a rough U shape. The ends were open, so the gas flow could blow MOF powder out of the holder and into the tube, and the holders could flip over inside the tube.

I made two new holders from aluminum rod on the lathe and manual mill. The copper tube has a 0.183" inner diameter, so I turned the 1/4" rod down to about 0.180", leaving roughly 0.0015" of clearance per side. Since the rod was 4–5" long and only 1/4" thick, I center-drilled the end and supported it with a live center, to keep the slender rod from deflecting away from the cutting tool.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-Holder_Lathe.jpg" alt="Aluminum rod being turned on the lathe">
  <figcaption>Turning the rod for the sample holders, with the end supported by a live center.</figcaption>
</figure>

After turning, I cut off the ends and moved to the manual mill, where I milled away the top half of the rod and then cut a channel down the middle for the sample. Unlike the old holders, the new ones don't flip inside the tube and don't let powder blow out.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-Sample_Holder.jpg" alt="Finished aluminum sample holder">
  <figcaption>One of the two finished sample holders.</figcaption>
</figure>

**Faster Cooling**

The tube was originally cooled by two very small fans, about half a watt each, mounted inside the glass tube at its ends. After desorbing at 160°C, it took a full 19 minutes for the tube to cool back to room temperature (25°C). That time is added to every cycle, which adds up quickly over a long test.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-DGS_Before.jpg" alt="Tube furnace inside the glass tube with the original small fans">
  <figcaption>The original setup: the tube furnace inside the glass tube, with the two small fans at its ends.</figcaption>
</figure>

I designed and 3D printed (in PLA) an air funnel to replace them. A 120 mm PC fan bolts to one end, and the funnel channels its air into the glass tube, around the copper tube. The outlet that holds the glass tube is offset below the fan's center, with the two axes parallel, so the glass tube sits closer to the table. If the tube slips off the funnel, which would usually only happen while someone is removing it, it has a shorter fall and is less likely to break. The PLA doesn't get too warm while the tube is heating.

The PhD student who runs the lab and I drilled a hole in the side of the funnel so the tubing to the gas analyzer could pass through. Moving the fans out of the glass tube cleaned up its inside and made loading and removing samples much easier. The new fan runs at the same voltage as the old ones, so it connected to the existing power supply with no other changes.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-Air_Funnel.jpg" alt="3D-printed air funnel with a 120 mm fan">
  <figcaption>The printed air funnel, with the 120 mm fan bolted to the back and the glass tube seated in the outlet.</figcaption>
</figure>

With the new funnel and fan, the tube now cools from 160°C to 35°C in about 4 minutes. That isn't a direct comparison with the old 19 minutes, which was the time to reach 25°C, and the last few degrees of cooling are always the slowest. To compare them, I estimated the old time to 35°C with Newton's law of cooling, T(t) − 25°C = 135°C · e^(−t/τ). If 19 minutes brought the tube within 1–2°C of room temperature, the time constant τ is about 3.9–4.5 minutes, so reaching 35°C would have taken about 10–12 minutes. By that estimate, the new setup cools roughly 2.5–3 times faster.

**Testing a Faster-Heating Tube**

To cut cycle time further, I also assembled a second tube furnace, the same size as the original but wound with thicker nichrome wire (22 AWG instead of the original 38 AWG) so it would heat faster. It's built the same way: a layer of Kapton tape on the copper tube, then the nichrome wire, then another layer of Kapton tape over the wire. I added a thermocouple at the middle of the tube, under the tape and between the windings rather than touching the wire, so it reads the tube's temperature instead of the heater's.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-Assembled_Tube.jpg" alt="Copper tube wrapped with thicker nichrome wire and Kapton tape">
  <figcaption>The new tube furnace with 22 AWG nichrome wire under the Kapton tape.</figcaption>
</figure>

Connected to our power supply, the new tube reached 90°C in under a minute, about twice as fast as the original tube, which takes about 2 minutes. But heating speed turned out not to be the bottleneck. The MOFs need time at temperature to release all of their adsorbed water vapor (CO₂ comes off more quickly, but both have to be fully desorbed), so a faster ramp doesn't shorten the desorb step by much. Cooling is different: every minute spent cooling adds directly to every cycle. The thicker wire leaves a larger gap between the two layers of Kapton tape, and the trapped air acts as an insulating layer, so the new tube was slower to cool (we didn't time the difference). Since cooling rate matters more than heating rate for this system, we decided to stay with the original, thinner wire.

**Testing Larger Tubes**

The lab may want to test more or larger samples in the future, so we also tested two tubes larger than the current 1/4" tube: a mid-size steel tube and a 5/8" OD copper tube, both 200 mm long like the original. In each tube, we switched the flow between CO₂ and nitrogen at 100, 200, and 500 SCCM and timed how long the analyzer took to go from 0 to 50,000 ppm CO₂ and back. In every case, the switch was nearly instant, even in the largest tube at the lowest flow rate (100 SCCM). So a bigger tube won't slow down gas switching; heating and cooling are what set the cycle time.

We ruled out the steel tube even though its gas switching was just as fast. Steel doesn't transfer heat nearly as well as copper, and this tube has a weld seam running along the inside. For now, the lab is still using the 1/4" copper tube, but the DGS will be able to take different tube sizes in the future.

<figure class="project-figure">
  <img src="assets/img/portfolio/06-different_tubes_sizes.jpg" alt="The three tubes tested, connected to the gas lines">
  <figcaption>The tubes tested: the current 1/4" copper tube inside the glass tube (top), the 5/8" copper tube (middle), and the steel tube (bottom).</figcaption>
</figure>

**Next Steps**

There are still more improvements planned for the DGS, and I'll add them here as they're finished.

- May 2026 - Present
- Lubner Group, Boston University · Laboratory Assistant

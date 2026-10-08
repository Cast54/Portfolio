---
title: Dynamic Gas System Chamber
subtitle: A vacuum chamber built to run direct air capture material through 5,000+ heating and cooling cycles, and the leak hunt that came with it.
image: assets/img/portfolio/03-full.jpg
alt: 

caption:
  title: Dynamic Gas System
  subtitle: Testing Chamber
  thumbnail: assets/img/portfolio/03-DGS_Thumbnail.jpg
---


**Overview**

The Dynamic Gas System (DGS) is a small vacuum chamber used to test metal-organic frameworks (MOFs), porous materials that capture CO₂. It's built for a 5,000-plus cycle degradation test, where the MOF adsorbs CO₂ and water vapor at ambient temperature (under 40°C), then desorbs under heat (60°C+) and vacuum (~1 mbar). Running that cycle thousands of times is how the lab finds out how the material's performance holds up over its working life.

There are two systems used to test these materials: the DGS Tube and the DGS Chamber. The Tube has two limitations the Chamber was built to address. First, the Tube can't pull a vacuum, so it instead flows pure nitrogen to simulate a CO₂-free environment. Second, MOFs are typically grown on a substrate like glass fiber or aluminum foam. Glass fiber is thin enough to fit in the 1/4" copper Tube, but a piece of aluminum foam, roughly 2" x 2" x 1", is not.

**Design**

I built the DGS Chamber to address both limitations, with the long-duration degradation tests in mind: everything about it is meant to reduce cycle time.

- **Port placement:** The chamber's two 1/8" NPT ports sit at opposite corners of the square design, so gas sweeps through the full volume as it cycles instead of leaving stagnant pockets that don't get purged.
- **Thin bottom:** The bottom of the chamber is only 1/16" thick, to maximize heating speed from a resistive heater attached underneath. We're also considering a Peltier element to heat and cool the MOFs, to cut cycle time further.
- **Minimal material:** The chamber uses as little material as possible to minimize thermal mass, so it heats up and cools down faster.

**Building the Chamber**

I modeled the chamber in Fusion 360 and used Fusion CAM to set it up for the CNC mill. I machined it on a Haas VF2 with a flat steel bed, securing a 4" x 1" x 16" aluminum bar with step clamps. The chamber needed tabs left uncut to hold it in place in the stock, since it wouldn't otherwise have stayed put during machining.

DGS Chamber in mill pics

After milling, I used a band saw to free the chamber from the stock, then set it up in a manual mill to drill and tap the two 1/8" NPT holes. From the CAD model, I made a DXF file to waterjet cut a lid for the chamber, and used that same file to laser cut a silicone gasket to seal it.

DGS Pics

**Testing and Troubleshooting the Seal**

With the chamber built, the PhD student who runs the carbon capture lab and I used the Alicat mass flow controllers from the DGS Tube to test for leaks under atmospheric pressure. Pumping nitrogen through the chamber, we measured a leak rate of roughly 1% at 500 SCCM, the top of the flow controllers' range. We moved on to vacuum testing, connecting the chamber to a vacuum pump on one end through a valve, with a gauge on the other.

vacuum setup pics

This is where most of our problems started. With the pump running, the chamber reached 0.8 mbar, but closing the valve to the pump let pressure rise quickly. Research pointed to the cause: silicone is highly gas-permeable, and we'd only used it because the lab already had a sheet on hand. We switched to a laser-cut nitrile (Buna-N) gasket instead. Concerned about flatness, I lapped both the lid and the chamber on a granite surface plate so the gasket's contact points would seal as evenly as possible. Neither change fixed the leak.

maybe more pics

**Finding the Leak**

After consulting with someone who designs vacuum chambers professionally, I ran an isopropanol (IPA) test on the whole system. The test works by temporarily plugging a leak with liquid IPA; as it evaporates and is drawn into the chamber, it produces a visible pressure spike on the pump gauge or vacrometer. Applying IPA to every likely leak point produced no spike, until I poured it onto the fitting for the vacrometer (a CPS VG200), which immediately sealed and held vacuum.

The IPA never fully evaporated into the chamber at that fitting; we think the leak there is small enough that the IPA's surface tension alone was plugging it. With that seal, the chamber held 2 mbar or less for six hours. Overnight, though, the IPA evaporated out to the atmosphere side, the leak reopened, and by morning the chamber had lost vacuum entirely (back above 100 mbar). We ordered a new gasket for the vacrometer, hoping that would solve it, but the leak persisted.

VGS pics

**Isolating the Valve**

Next we removed the gauge entirely to cut down on possible leak points and turned to the NPT valves as the next suspect. IPA on the valves hadn't shown a spike in the earlier round, but we tried again, confident the chamber itself was sound. With the chamber held at 0.7 mbar by the pump, pouring IPA into a valve handle held upside down, then flipping it upright, spiked the pressure to over 10 mbar. Once again, the NPT fittings and the chamber's own gasket showed nothing.

**IPA test video**

We're not sure yet why the valves sealed in the earlier test but not this one; our best guess is that of the two identical 1/8" NPT valves, only one is actually good. Either way, we believe the chamber itself is capable of holding a vacuum sufficient for the long-duration degradation tests, we just need fittings that won't leak over time.

**Next Steps**

Once the fittings are sorted, the next tests are to see how the chamber holds vacuum while heated by the resistive heater on the bottom, and how fast and efficiently it can cycle gases. After that, it'll be ready for its intended purpose.



{:.list-inline}
- May 2026 - Present
- Lubner Group, Boston University · Laboratory Assistant


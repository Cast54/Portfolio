---
title: Circuit Printing
subtitle: Expanding a fully automated robotic cell that mills, ink-writes, and assembles custom circuits.
image: assets/img/portfolio/02-CircuitPrint_Thumbnail.jpg
alt: Keep Exploring

caption:
  title: Circuit Printing
  subtitle: Automated Manufacturing
  thumbnail: assets/img/portfolio/02-CircuitPrint_Thumbnail.jpg
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
 
The Circuit Printing project was part of the Advanced Manufacturing course at BU. Every group in the class worked in the Automated Manufacturing Lab (ADML), where the goal was to fully automate the manufacturing of a component or product. My group of six chose circuit printing.
 
**The ADML**
 
The ADML is a robotic manufacturing cell made up of two Haas CM-1 CNC mills, three UR5 robotic arms, and a conveyor belt connecting each station. Two of the stations each pair a mill with a UR5. Each mill has an opening in its side that lets the robot load and unload stock from a pneumatic vise. The robot then places the milled stock on a tray, which it loads onto (or unloads from) the conveyor.
 
The last station has the third UR5, which takes the trays of milled parts, assembles them, and sets the finished product aside. This robot can also pick up syringes that dispense conductive silver ink onto the parts.

_Take pic of ADML!_
<figure class="project-figure">
  <img src="assets/img/portfolio/02-ADML.jpg" alt="The ADML robotic cell">
  <figcaption>The ADML: two CNC mills, three UR5 arms, and the conveyor connecting them.</figcaption>
</figure>
 
**How Circuit Printing Worked**
 
The ADML already had a circuit printing setup, but it was very limited, so our goal was to expand it. Circuit printing ran on three programs: automated CAD (with a GUI), automated CAM, and the BU Manufacturing Execution System (BUMES).
 
A user designs a basic circuit in the GUI by entering the dimensions of the HDPE stock and placing each component on the board. The GUI had a set list of components: an LED, a battery, a button, and a microcontroller. After the components are placed and connected in the GUI's 2D layout, the automated CAD program generates a Fusion model of the stock with pockets to hold each component and channels for the conductive ink. Automated CAM then generates the toolpaths for the CM-1 mills, and the G-code is uploaded to the machines.
 
From there, BUMES runs the whole system. It sends the UR5s preset commands to load the mills with stock, run the mills, and place the milled boards onto the conveyor. The third arm then uses a pneumatic syringe to direct ink write (DIW) the conductive traces into the milled channels, and a second syringe with a rubber suction tip to pick up each component and place it on the board.
 
<figure class="project-figure">
  <img src="assets/img/portfolio/02-BUMES.jpg" alt="Circuit printing system running through BUMES">
  <figcaption>The circuit printing system controlled through BUMES.</figcaption>
</figure>
 
**Expanding the System**
 
We felt the component list was too limited, so we added two new parts: a potentiometer and a buzzer. Adding them meant working through every layer of the system:
 
- **CAD and GUI:** We modeled each component and programmed its dimensions, pin locations, and pin polarities into the GUI.
- **Automated CAD and CAM:** We verified that both programs correctly generated pockets, ink channels, and toolpaths for the new parts.
- **Component tray:** We built a new tray to hold the new components, sitting next to the existing tray.
- **Pick and place:** We added each component's location and orientation to the pick-and-place program in BUMES, so the UR5 would know where to find it.
- **Tuning:** We tuned the system until the robot picked and placed every component accurately and consistently.
 
<figure class="project-figure">
  <div class="video-wrapper">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/T_Waw3J1nn0?si=2UEa46Eq5SMb7qkG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
  <figcaption>The UR5 assembling a printed circuit.</figcaption>
</figure>
 
**Problem Solving**
 
Although most of the circuit printing software already existed, getting our components to work was a constant problem-solving process.
 
*Picking up the potentiometer.* The suction tip had trouble picking up the potentiometer because of the slot down its middle that the slider travels in, which kept the tip from forming a seal. We first planned to 3D print caps to give the suction tip a flat surface to grab, but the much simpler solution was to put tape over the top of the potentiometer.
 
<figure class="project-figure">
  <img src="assets/img/portfolio/02-Potentiometer_Tape.jpg" alt="Taped potentiometer">
  <figcaption>Tape over the potentiometer's slot gave the suction tip a surface to seal against.</figcaption>
</figure>
 
*Shared code.* Several other teams used the same system, and even though our code lived in a separate folder, other groups would sometimes change it. At one point one of our files was deleted, which stopped the entire system from working.
 
*Pick-and-place accuracy.* Our biggest challenge was getting pick and place to work reliably. The robot would pick up a component and set it down slightly off from where it belonged. The program used a palletizing pattern for pickup: we taught the robot the positions of the first and last components in the tray, and it interpolated the positions in between. To correct where a component landed on the circuit, we adjusted where it was picked up, often by less than 1 mm. We had to tune the first and last positions for every component type, including the original ones, since the robot wasn't placing those accurately either.
 
<figure class="project-figure">
  <img src="assets/img/portfolio/02-Component_Tray.jpg" alt="Custom component tray installed next to existing component try">
  <figcaption>The custome component tray for the new components, installed next to the existing component tray.</figcaption>
</figure>
 
*Conductive ink.* The conductive ink is a shear-thinning, yield-stress paste made with pure silver powder, which we mixed ourselves. It only lasted about a day before hardening, so we only made it when we were confident the components were lining up correctly. Because the syringe was driven pneumatically, small changes in the ink's viscosity from batch to batch meant it would under- or over-extrude, even at the same pressure. Cutting off the end of the syringe tip to slightly enlarge the opening gave us much more consistent extrusion.
 
<figure class="project-figure">
  <img src="assets/img/portfolio/02-Silver_Ink.jpg" alt="Filling conductive silver ink into syringe">
  <figcaption>Placing conductive silver ink into syringe.</figcaption>
</figure>
 
*An unexplained drop.* One day, the arm moved a few millimeters lower than usual and damaged the suction tip on the second syringe. We were able to replace the tip, but we never found the cause. The code hadn't changed, the pneumatic vise holding the circuit hadn't moved, the syringe hadn't shifted in the robot's gripper, and the UR5 recalibrates itself at the start of every run anyway. To protect the tip and the components, we changed the code so the arm offsets itself 2 to 3 mm upward after calibration.
 
**Results**
 
Once we solved the problems with the ink, calibration, extrusion, code, and suction tip, we were able to design a circuit in the GUI using our new components, generate the CAD and CAM automatically in Fusion, and run a fully automated production and assembly line that milled and direct ink wrote custom circuits. Our added components also expand what the ADML can build, giving future classes and groups more options for producing their own custom circuits.
 
<figure class="project-figure">
  <img src="assets/img/portfolio/02-Circuits.jpg" alt="Finished printed circuits">
  <figcaption>The finished, fully automated printed circuits with their CAD models.</figcaption>
</figure>

{:.list-inline}
- January 2026 - May 2026
- Advanced Manufacturing - ME500


